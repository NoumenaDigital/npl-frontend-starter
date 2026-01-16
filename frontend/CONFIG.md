# Configuration

## AUTH

Defined by LOGIN_MODE environment variable.

- DEV MODE: Uses custom login form with `/token` endpoint
- OIDC: Uses _Resource Owner Password Credentials (ROPC)_ OIDC/OAuth2.0 authentication flow (e.g. Keycloak "Direct 
    Access grant") and custom login form with `/protocol/openid-connect/token` endpoint. The user provides
    username/password directly to the client, and the client sends username and password to the token endpoint of the
    Identity Provider. For use cases where risks associated with credentials handling by the app are limited, e.g.
    direct API login.
- KEYCLOAK: Uses _Authorization Code_ OIDC/OAuth2.0 authentication flow, i.e. user login via redirect to a login form
    provided by the Identity Provider. Standard flow for web apps (confidential/public clients). Best for MFA, browser
    session and SSO support.

References:
[ROPC](https://auth0.com/docs/get-started/authentication-and-authorization-flow/resource-owner-password-flow)
and
[Authorization Code](https://auth0.com/docs/get-started/authentication-and-authorization-flow/authorization-code-flow)
flows (as powered by auth0.com)

## API

Defined by DEPLOYMENT_TARGET environment variable.

- LOCAL:
    - NPL Engine running in docker running locally
- NOUMENA CLOUD:
    - NPL Engine running on NOUMENA CLOUD

## Combinations

1. Dev mode: LOCAL deployment target + DEV MODE login
2. Local user management (with ROPC authentication flow): LOCAL deployment target + OIDC login
3. Complete user management in the Identity Provider, prepare for cloud deployment (with Authorization Code
    authentication flow): LOCAL deployment target + KEYCLOAK login
4. Cloud deployment (with ROPC authentication flow): NOUMENA CLOUD deployment target + OIDC login
5. Cloud deployment (with Authorization Code authentication flow): NOUMENA CLOUD deployment target + KEYCLOAK login
