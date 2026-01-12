# Configuration

## AUTH

Defined by LOGIN_MODE environment variable.

- DEV MODE:
    - uses custom login form with /token endpoint
- OIDC:
    - uses custom login form with /protocol/openid-connect/token endpoint
- KEYCLOAK:
    - uses keycloak lib (deeper integration with keycloak, higher security standards)

## API

Defined by DEPLOYMENT_TARGET environment variable.

- LOCAL:
    - NPL Engine running in docker running locally
- NOUMENA CLOUD:
    - NPL Engine running on NOUMENA CLOUD

## Combinations

1. dev mode: LOCAL deployment target + DEV MODE login
2. local user management: LOCAL deployment target + OIDC login
3. complete user management, prepare for cloud deployment: LOCAL deployment target + KEYCLOAK login
4. cloud deployment: NOUMENA CLOUD deployment target + OIDC login
5. cloud deployment, with keycloak integration: NOUMENA CLOUD deployment target + KEYCLOAK login
