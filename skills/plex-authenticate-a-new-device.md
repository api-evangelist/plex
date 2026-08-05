---
name: Authenticate a new device with Plex using the JWT PIN flow
description: Register an Ed25519 public key, link a device with a PIN, exchange it for a 7-day Plex JWT, and keep the token refreshed — the credential every Plex Media Server call depends on.
api: openapi/plex-media-server-openapi.json
operations:
  - getIdentity
  - securityPostToken
  - securityGetResources
---

# Authenticate a new device with Plex using the JWT PIN flow

Plex Media Server itself only ever sees one credential: the `X-Plex-Token` header.
Everything below is about *obtaining* that value from `plex.tv`. The token endpoints
live on the plex.tv cloud API (`https://clients.plex.tv/api/v2`), not on the media
server, so they are not operations in the Plex Media Server OpenAPI — they are
documented in the spec's "Authenticating with Plex" section and captured in
`authentication/plex-authentication.yml`.

Since September 2025 Plex recommends **JWT authentication** over the legacy
long-lived token. JWTs expire after 7 days and are signed with a device-held
Ed25519 key.

## Steps

1. **Generate a device key pair.** Ed25519 (`kty: OKP`, `crv: Ed25519`,
   `alg: EdDSA`). RSA with `RS256` is also accepted. Keep the private key on the
   device; only the JWK public half ever leaves it.

2. **Create a PIN carrying your JWK.**
   `POST https://clients.plex.tv/api/v2/pins` with header
   `X-Plex-Client-Identifier` and a body containing your `jwk` and `"strong": true`.
   Response carries the PIN `id` and `code`.

3. **Send the user to authenticate.**
   `https://app.plex.tv/auth#?clientID=<clientIdentifier>&code=<pinCode>&context[device][product]=<your product>&forwardUrl=<your return url>`
   (URL-encode the bracketed context keys). For 4-digit PINs use
   `https://plex.tv/link/?pin=<code>` instead.

4. **Exchange the PIN.**
   `GET https://clients.plex.tv/api/v2/pins/<pinID>?deviceJWT=<signedJWT>`.
   The device JWT you sign must carry `"aud": "plex.tv"`,
   `"iss": "<clientIdentifier>"`, and `kid` + `alg` in the header. The Plex JWT
   comes back in the `authToken` field.

5. **Refresh before day 7 — three calls.**
   1. `GET https://clients.plex.tv/api/v2/auth/nonce` (with
      `X-Plex-Client-Identifier`) — the nonce is valid for **5 minutes**.
   2. Sign a device JWT containing that nonce, your `scope`, `aud: plex.tv` and
      `iss: <clientIdentifier>`.
   3. `POST https://clients.plex.tv/api/v2/auth/token` to receive the new Plex JWT.

   The `scope` field is a comma-separated list of **account claims to embed in the
   issued JWT**, not API permissions: `username`, `email`, `friendly_name`,
   `restricted`, `anonymous`, `joinedAt`. Ask only for what you use. See
   `scopes/plex-scopes.yml`.

6. **Verify against the server — `getIdentity`.**
   `GET /identity` on the target Plex Media Server confirms reachability and returns
   its `machineIdentifier`. `securityGetResources`
   (`GET /security/resources`) returns the source connection information for that
   server.

7. **Mint a transient token when handing off — `securityPostToken`.**
   `POST /security/token` (`securityPostToken`) issues a short-lived transient token
   for scoped delegation, so you can hand playback to another component without
   sharing the account token.

## Rules

- **Verify signatures against the published JWKS**, `https://plex.tv/api/v2/auth/keys`
  — an Ed25519 `EdDSA` key set. It is advertised as `jwks_uri` by
  `https://plex.tv/.well-known/openid-configuration`.
- **Never send the token as a query parameter in production.** Plex's own docs warn
  it leaks into server logs and browser history. Use the `X-Plex-Token` header.
- Send `X-Plex-Client-Identifier` on every request, including the auth calls. It is
  the identity the PIN and JWK are bound to; change it and the device is a new
  device.
- The OAuth 2.1 endpoints published at `https://plex.tv/.well-known/oauth-authorization-server`
  are **not** for this flow. They exist only to authorize the Plex MCP server at
  `https://plex.tv/internal/mcp` with the single scope `mcp`.
- Legacy long-lived tokens still work and are still what the Plex Web App carries.
  They are the right choice for a personal script and the wrong choice for anything
  distributed.
