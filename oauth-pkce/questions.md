# OAuth PKCE

## Overview

OAuth 2.0 with PKCE (Proof Key for Code Exchange, RFC 7636) is an extension to the OAuth 2.0 Authorization Code flow that protects public clients (e.g., mobile apps, SPAs) against authorization code interception attacks. Instead of a static client secret, PKCE uses a dynamically generated code verifier and code challenge.

## Conceptual Questions

- What is OAuth 2.0?
- What problem does OAuth 2.0 solve?
- What is an authorization server?
- What is a resource server?
- What is a client in OAuth?
- What is a public client?
- What is a confidential client?
- What is an authorization code?
- What is the Authorization Code flow?
- What is the Implicit flow and why is it deprecated?
- What is the Client Credentials flow?
- What is the Device Authorization flow?
- What is PKCE?
- What problem does PKCE solve?
- What is a code verifier?
- What is a code challenge?
- What is the S256 method?
- What is the plain method and why is it discouraged?
- What is a redirect URI?
- What is scope?
- What is a state parameter?
- What is a nonce?
- What is an access token?
- What is a refresh token?
- What is the difference between an access token and a refresh token?
- What is token expiration?
- What is token rotation?
- What is a bearer token?
- What is the Authorization header format for bearer tokens?
- What is OpenID Connect (OIDC)?
- How does OIDC extend OAuth 2.0?
- What is an ID token?
- What is the difference between an access token and an ID token?
- What is a UserInfo endpoint?

## Deep Dive Questions

- Walk through the complete OAuth PKCE flow step by step.
- How is the code verifier generated?
- What are the character set and length requirements for the code verifier?
- How is the code challenge derived from the code verifier using S256?
- What is the S256 formula: `BASE64URL(SHA256(ASCII(code_verifier)))`?
- What parameters does the authorization request include?
- What is `response_type=code`?
- What is `client_id`?
- What is `redirect_uri`?
- What is `scope`?
- What is `state`?
- What is `code_challenge`?
- What is `code_challenge_method`?
- What does the authorization server return after user authentication?
- What parameters does the token request include?
- What is `grant_type=authorization_code`?
- What is the `code` parameter in the token request?
- What is `code_verifier` in the token request?
- How does the authorization server verify the code_verifier?
- What response does the authorization server return for a successful token request?
- What is the `token_type` field in the token response?
- What is the `expires_in` field?
- What is the `refresh_token` field?
- How does the client use the access token to call the resource server?
- How does the client use the refresh token to obtain a new access token?
- What is the refresh token request?
- What is the difference between authorization server and token introspection endpoint?
- What is token introspection (RFC 7662)?
- What is token revocation (RFC 7009)?
- What is the difference between online and offline access?
- What are PKCE security properties compared to the plain Authorization Code flow?

## Why Questions

- Why does PKCE exist when the Authorization Code flow already exists?
- Why can't a public client use a client secret?
- Why is the Implicit flow deprecated?
- Why is S256 preferred over the plain method?
- Why is the code verifier never sent in the authorization request?
- Why is the state parameter needed even with PKCE?
- Why is the redirect URI validated on both the authorization request and the token request?
- Why does the authorization code have a short lifetime?
- Why does the access token have a short lifetime?
- Why use a refresh token instead of simply re-running the authorization flow?
- Why is refresh token rotation important?
- Why does PKCE not rely on TLS alone for security?

## Coding Questions

- Implement code verifier generation (secure random, base64url encoding).
- Implement code challenge derivation using S256.
- Implement the authorization URL builder with all required parameters.
- Implement the token request (exchange authorization code for tokens).
- Implement the refresh token request.
- Implement state parameter validation to prevent CSRF.
- Implement an OAuth callback handler that validates the authorization response.
- Implement secure token storage for a browser-based app.
- Implement a token refresh interceptor that automatically refreshes expired tokens.
- Implement token revocation.

## Edge Cases

- What happens when the state parameter in the callback does not match the stored state?
- What happens when the code_verifier does not match the code_challenge?
- What happens when the authorization code is intercepted and used by an attacker?
- What happens when the access token expires and no refresh token is available?
- What happens when the refresh token is also expired?
- What happens when the redirect URI in the token request does not match the authorization request?
- What happens when the authorization code is replayed?
- What happens when the user denies authorization?
- What happens when the authorization server returns an error response?

## Debugging Scenarios

- Token request fails with `invalid_grant`. What are the possible causes?
- Authorization code is returned but the token exchange fails. How do you debug?
- Access token is rejected by the resource server. What do you check?
- Refresh token rotation causes sessions to expire unexpectedly. Why?
- State parameter validation fails intermittently. What is the likely cause?
- Users are redirected to the authorization server repeatedly (infinite loop). Why?

## System Design Questions

- Design an OAuth authorization server that supports PKCE.
- Design a session management system for a SPA that uses OAuth PKCE.
- Design a token refresh strategy that minimizes re-authentication prompts.
- Design a multi-tenant OAuth system that routes to different authorization servers by tenant.

## Related Topics

- [JWT](../jwt/questions.md)
- [WebSockets](../websockets/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [System Design](../system-design/questions.md)
