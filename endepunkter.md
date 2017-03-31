# Endepunkter

En kort beskrivelse av FIA STS' endepunkter.

## Discovery endpoint

Discovery-endepunktet har sin egen [spesifikasjon](http://openid.net/specs/openid-connect-discovery-1_0.html), brukes til å hente metadata om STS-en, det være seg blant annet hvilke scopes, grant types, claims, klientautentiseringsmekanismer og signeringsalgoritmer som støttes.

## Authorize endpoint

Authorize-endepunktet er definert i [OpenID Connect Core 1.0-spesifikasjonen](http://openid.net/specs/openid-connect-core-1_0.html#AuthorizationEndpoint), og brukes til å forespørre tokens eller autorisasjonskoder via frontkanalen, og vil innledningsvis involvere autentisering av brukeren.

## Token endpoint

Token-endepunktet er definert i [OpenID Connect Core 1.0-spesifikasjonen](http://openid.net/specs/openid-connect-core-1_0.html#TokenEndpoint), og brukes til å programmatisk forespørre tokens, og støtter granttypene authorization code, client credentials og refresh token, i tillegg til resource owner password som ikke er relevant for FIA STS.

## Userinfo endpoint

UserInfo-endepunktet er definert i [OpenID Connect Core 1.0-spesifikasjonen](http://openid.net/specs/openid-connect-core-1_0.html#UserInfo), og brukes til å hente identitetsinformasjon om en bruker, i henhold til definerte scopes i access token-et som benyttes til å få tilgang.

## Introspection endpoint

Introspection-endepunktet har sin egen [spesifikasjon](https://tools.ietf.org/html/rfc7009), og brukes til å validere reference tokens. I retur får man valideringsresultat, samt eventuelle korresponderende claims som ligger lagret i STS-ens operasjonelle database.

Tilgang til endepunktet forutsetter autentisering ved hjelp av en API-ressurshemmelighet.

## Revocation endpoint

Revocation-endepunktet har sin egen [spesifikasjon](https://tools.ietf.org/html/rfc7009), og brukes til å tilbakekalle reference tokens og refresh tokens. Access tokens som ikke er reference tokens, men som da altså er self-contained access tokens, kan ikke tilbakekalles.
