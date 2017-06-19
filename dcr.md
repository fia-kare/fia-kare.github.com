

# Klientregistrering
FIA tilbyr et REST API for administrasjon av klienter og ressurser.

Klienter og API-ressurser er underordnet en konfigurasjonseier. En konfigurasjonseier opprettes per organisasjon, eller del av organisasjonen, og kan kun manipulere data for sine klienter og ressurser.

![Konfigurasjonseier](https://cdn.rawgit.com/fia-sikkerhet/fia-sikkerhet.github.com/fa74b598/images/Konfigurasjonseier.png)

## API-ressurs

En API-ressurs er et tjenestegrensesnitt som STS-en beskytter. I motsetning til identitetsressurser kan en API-ressurs være tilknyttet flere scopes. API-ressursen kan være konfigurert med en API secret, som videre er en forutsetning for å kunne bruke utstedt reference token mot Introspection-endepunktet.

API-ressurser kan være tilknyttet flere claims, som representeres i utstedte access tokens.

### Input

| Parameter | Datatype | Påkrevd | Beskrivelse |
| --- | --- | --- | --- |
| api_respource_id | string | Kun ved oppdatering | |
| name | string | Ja | Må være unikt |
| display_name | string | Nei | For bruk i consent screen |
| description | string | Nei | For bruk i consent screen |
| authorization_scopes | string[] | Nei | |
| secrets | secret[] | Nei | Secrets for bruk mot introspection endpoint - type må være shared_secret eller x509_cert_base64. Expiration (UTC i format: "dd.MM.yyyy") lik null betyr at hemmeligheten ikke utløper. |

#### secret
```json
{
  "type": "shared_secret",
  "value": "[long_random_string]",
  "expiration": "23.11.2099"
}
```

### Output

| Parameter | Datatype | Beskrivelse |
| --- | --- | --- |
| api_respource_id | string | Generert id |
| name | string | |
| display_name | string | |
| description | string | |
| authorization_scopes | string[] | |

### Tildeling av autorization_scopes til eksterne klienter
Det er mulig å gi eksterne klienter tilgang til autorisasjons-scopes for Api Ressurser. En ekstern klient er en klient som eies av en annen Configuration Owner enn den som eier API Ressursen.

Endepunktet for å registrere, endre og hente ut autorisasjonsskop satt på eksterne klienter er
```
https://{sts_adresse}/api/connect/externalScope/register
```

Endepunktet støtter POST, PUT og DELETE

#### POST
Legg til et scope for en klient. Bruk følgende parametre i body.
```json
{
"external_client_id": "[client_id]",
"scope": "[navn på scope, inkludert configuration owner prefix]",
"api_resource_id_for_scope": "[id til api resource som har scopet som en autorization_scope]"
}
```

Returnerer "true" ved suksess, "false" om noe feiler. 

#### DELETE
Slett et eksternt scope.     	

```json
{
"external_client_id": "[client_id]",
"scope": "[navn på scope, inkludert configuration owner prefix]",
"api_resource_id_for_scope": "[id til api resource som har scopet som en autorization_scope]"
}
```

Returnerer "true" ved suksess, "false" om noe feiler. 


#### GET
Hent ut en liste med alle eksterne client_id-er som har blitt tildelt et scope. Merk at egne clienter med dette scopet ikke returneres.

```
?scope=[navn på scope, inkludert configuration owner prefix]
```

Det er ikke mulig:
* å slette api resources med scope som er tildelt eksterne klienter.
* å fjerne scopes fra en api ressures som er tildelt en eller fler eksterne klienter.


## Klient

En klient er en applikasjon som kan forespørre tokens fra STS-en. De mest sentrale informasjonselementene for en klient er som følger:
-	En unik klientidentifikator
-	En hemmelighet, hvis nødvendig
-	Tillatte grant types
-	URL-er til hvilke nettleseren skal omdirigeres (tilbake) til etter å ha vært innom STS-en for inn- eller utlogging
-	Tillatte scopes

### Input

| Parameter | Datatype | Påkrevd | Defaultverdi | Beskrivelse |
| --- | --- | --- | --- | --- |
| client_id | string | Kun ved oppdatering | | OIDC-standard |
| client_name | string | Ja | | OIDC-standard - Må være unikt |
| redirect_uris | string | Nei | | OIDC-standard - Må være https |
| grant_types | string[] | Ja | | OIDC-standard - authorization_code, client_credentials, hybrid, implicit |
| absolute_refresh_token_lifetime | int | Nei | 2 592 000 | |
| access_token_lifetime | int | Nei | 3600 | |
| access_token_type | string | Nei | jwt | jwt, reference |
| allow_access_tokens_via_browser | boolean | Nei | false | |
| allow_refresh_token | boolean | Nei | false | |
| always_include_user_claims_in_identity_token | boolean | Nei | false | |
| always_send_client_claims | boolean | Nei | false | |
| authorization_code_lifetime | int | Nei | 300 | |
| identity_provider_restrictions | string[] | Nei | | |
| identity_token_lifetime | int | Nei | 300 | |
| logout_uri | string | Hvis redirect-basert grant-type | | |
| post_logout_redirect_uris | string[] | Nei | | |
| refresh_token_expiration | string | Nei | absolute | absolute, sliding |
| refresh_token_usage | string | Nei | one_time_only | one_time_only, reuse |
| require_client_secret | boolean | Nei | false | |
| sliding_refresh_token_lifetime | int | Nei | 1 296 000 | |
| client_claims | client_claim[] | Nei | | |
| allowed_scopes | string[] | Nei | | Tillatte scopes - globale eller definert under API Resources |
| secrets | secret[] | Nei | | Ved behov for å autentisere klienten mot STS-en - type må være shared_secret eller x509_cert_base64. Expiration (UTC i format: "dd.MM.yyyy") lik null betyr at hemmeligheten ikke utløper. |

#### client_claim
```json
{
  "type": "org_no",
  "value": "123456789"
}
```

#### secret
```json
{
  "type": "shared_secret",
  "value": "[long_random_string]",
  "expiration": null
}
```

### Output

| Parameter | Datatype | Beskrivelse |
| --- | --- | --- |
| client_id | string | OIDC-standard - Generert id |
| client_name | string | OIDC-standard |
| redirect_uris | string | OIDC-standard  |
| grant_types | string[] | OIDC-standard |
| absolute_refresh_token_lifetime | int | |
| access_token_lifetime | int | |
| access_token_type | string | |
| allow_access_tokens_via_browser | boolean | |
| allow_refresh_token | boolean | |
| always_include_user_claims_in_identity_token | boolean | |
| always_send_client_claims | boolean | |
| authorization_code_lifetime | int | |
| identity_provider_restrictions | string[] | |
| identity_token_lifetime | int | |
| logout_uri | string | |
| post_logout_redirect_uris | string[] | |
| refresh_token_expiration | string | |
| refresh_token_usage | string | |
| require_client_secret | boolean | |
| sliding_refresh_token_lifetime | int | |
| client_claims | client_claim[] | |
| allowed_scopes | string[] | |
