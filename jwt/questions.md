# JWT

## Overview

JSON Web Token (JWT, RFC 7519) is a compact, URL-safe token format used to represent claims between parties. A JWT consists of three Base64URL-encoded parts separated by dots: a header, a payload, and a signature. JWTs are commonly used for authentication and authorization in web APIs.

## Conceptual Questions

- What is a JWT?
- What problem does JWT solve?
- What are the three parts of a JWT?
- What is the JWT header?
- What is the JWT payload?
- What is the JWT signature?
- What is a claim?
- What are registered claims?
- What is the `iss` (issuer) claim?
- What is the `sub` (subject) claim?
- What is the `aud` (audience) claim?
- What is the `exp` (expiration time) claim?
- What is the `nbf` (not before) claim?
- What is the `iat` (issued at) claim?
- What is the `jti` (JWT ID) claim?
- What are public claims?
- What are private claims?
- What is Base64URL encoding?
- How does Base64URL differ from Base64?
- What is JWS (JSON Web Signature)?
- What is JWE (JSON Web Encryption)?
- What is the difference between JWS and JWE?
- What is JOSE (JSON Object Signing and Encryption)?
- What is HS256?
- What is RS256?
- What is ES256?
- What is the difference between symmetric and asymmetric JWT signing?
- What is a JWKS (JSON Web Key Set)?
- What is the JWKS endpoint?
- What is a key ID (kid) header parameter?
- What is JWT used for in OAuth?
- What is the difference between opaque tokens and JWTs?
- What is a JWT access token?
- What is a JWT ID token (in OIDC)?

## Deep Dive Questions

- Describe the exact structure of a JWT string.
- Describe the JWT header fields.
- What is the `alg` header parameter?
- What is the `typ` header parameter?
- What is the `kid` header parameter?
- What is the `x5t` header parameter?
- Describe the JWT payload structure.
- How is the JWT signature computed for HS256?
- What is the HMAC-SHA256 input for the signature?
- How is the JWT signature computed for RS256?
- What is the RSA-SHA256 input for the signature?
- How does ES256 (ECDSA with P-256 and SHA-256) sign a JWT?
- How does a JWT verifier validate an HS256 JWT?
- How does a JWT verifier validate an RS256 JWT?
- What is the public key used for in RS256 verification?
- How does a relying party retrieve a public key from a JWKS endpoint?
- What is the `alg=none` vulnerability?
- What is the key confusion attack (RS256 to HS256)?
- What is a JWT signing key rotation strategy?
- What is the `kid` header used for during key rotation?
- How do you revoke a JWT?
- What is a JWT denylist and what are its trade-offs?
- What is a short-lived JWT and how does it reduce the need for revocation?
- What is the JWT `exp` claim check and what happens when it fails?
- What is clock skew and how should validators account for it?
- What is nested JWT (JWT within JWE)?
- Describe the JWE compact serialization format.

## Why Questions

- Why use JWT instead of session cookies?
- Why use JWT instead of opaque tokens?
- Why use RS256 instead of HS256 in a distributed system?
- Why use ES256 instead of RS256?
- Why is the `alg=none` option dangerous?
- Why is the key confusion attack possible?
- Why is JWT revocation hard?
- Why should JWT access tokens be short-lived?
- Why should the JWT audience (`aud`) claim be validated?
- Why should the JWT issuer (`iss`) claim be validated?
- Why use a JWKS endpoint instead of static public key distribution?
- Why does JWT not encrypt claims by default?
- Why is storing JWTs in localStorage a security risk?
- Why are HttpOnly cookies often preferred over localStorage for JWT storage?

## Coding Questions

- Implement JWT parsing (split on `.`, base64url-decode each part, parse JSON).
- Implement JWT validation: verify signature, check `exp`, check `iss`, check `aud`.
- Implement HS256 JWT signing.
- Implement HS256 JWT verification.
- Implement RS256 JWT signing using an RSA private key.
- Implement RS256 JWT verification using an RSA public key.
- Implement JWKS endpoint fetching and public key extraction.
- Implement key rotation: pick the correct key using `kid`.
- Implement a JWT middleware for an HTTP server.
- Implement a JWT denylist using Redis.
- Implement a JWT refresh flow.

## Edge Cases

- What happens when the JWT has expired (`exp` in the past)?
- What happens when `nbf` is in the future?
- What happens when the `aud` claim does not match the expected audience?
- What happens when the `iss` claim does not match the expected issuer?
- What happens when the signature verification fails?
- What happens when the `alg` header is `none`?
- What happens when the `kid` in the JWT header does not match any key in the JWKS?
- What happens when the JWKS endpoint is down during token validation?
- What happens when clock skew causes a valid token to appear expired?
- What happens when a JWT is replayed after it has been used?

## Debugging Scenarios

- An API returns 401 Unauthorized for a valid JWT. What do you check?
- JWT validation fails intermittently for some users. What could cause it?
- After key rotation, all tokens are rejected. Why?
- A JWT is valid on one service but rejected by another. What is the likely cause?
- The `exp` claim is correct but tokens are being rejected as expired. What is the likely cause (clock skew)?
- A service is vulnerable to the `alg=none` attack. How do you fix it?

## System Design Questions

- Design a JWT-based authentication system for a microservices architecture.
- Design a JWT key rotation strategy with zero downtime.
- Design a token revocation system for JWTs.
- Design a multi-tenant JWT system where different tenants use different signing keys.
- Design an API gateway that validates JWTs and forwards claims to upstream services.

## Related Topics

- [OAuth PKCE](../oauth-pkce/questions.md)
- [WebSockets](../websockets/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [System Design](../system-design/questions.md)
