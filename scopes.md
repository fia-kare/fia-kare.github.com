# Scopes

| Navn | Claims | Beskrivelse |
| --- | --- | --- |
| openid | | OIDC standard scope - obligatorisk ved bruk av OIDC |
| profile | name, family_name, given_name, middle_name | OIDC standard scope |
| `helseid://scopes/client/dcr` | | Dynamic client registration |
| `helseid://scopes/client/organization_number` | `helseid://claims/client/organization_number` | |
| `helseid://scopes/hpr` | `helseid://claims/hpr/authorization`, `helseid://claims/hpr/hpr_number` | |
| `helseid://scopes/hpr/hpr_number` | `helseid://claims/hpr/hpr_number` | |
| `helseid://scopes/identity/assurance_level` | `helseid://claims/identity/assurance_level` | |
| `helseid://scopes/identity/pid` | `helseid://claims/identity/pid` | |
| `helseid://scopes/identity/pid_pseudonym` | `helseid://claims/identity/pid_pseudonym` | |
| `helseid://scopes/identity/security_level` | `helseid://claims/identity/security_level` | |

Se [claims](claims.md) for nærmere beskrivelse av disse.
