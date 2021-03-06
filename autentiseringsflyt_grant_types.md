# Autentiseringsflyt og grant types

Grant types, eller autentiseringsflyt, er ulike måter for hvordan en klient kan samhandle med STS-en.

OpenID Connect 1.0 definerer 3 forskjellige autentiseringsflyter (eksterne lenker):

-	[Authorization code flow](http://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth)
-	[Implicit flow](http://openid.net/specs/openid-connect-core-1_0.html#ImplicitFlowAuth)
-	[Hybrid flow](http://openid.net/specs/openid-connect-core-1_0.html#HybridFlowAuth)

OAuth 2.0 definerer 6 grant types (eksterne lenker):

-	[Authorization code grant](https://tools.ietf.org/html/rfc6749#section-4.1)
-	[Implicit grant](https://tools.ietf.org/html/rfc6749#section-4.2)
-	[Resource owner password credentials grant](https://tools.ietf.org/html/rfc6749#section-4.3)
-	[Client credentials grant](https://tools.ietf.org/html/rfc6749#section-4.4)
-	[Extension grant](https://tools.ietf.org/html/rfc6749#section-4.5)
-	[Refresh token](https://tools.ietf.org/html/rfc6749#section-6)

FIA STS implementerer, eller tilrettelegger for, det som kombinert blir 7 grant types (autentiseringsflyter), som vil kort forklares her.

## Implicit grant

Implicit flow er primært tiltenkt browserbaserte applikasjoner, det være seg enten for brukerautentisering alene, eller både autentiserings- og access token-forespørsler, der det sistnevnte vil gjelde for JavaScript-applikasjoner. En SPA (Single Page Application) er det typiske brukstilfellet for implicit flow.

Ved implicit flow vil tokens bli sendt via browseren, altså frontkanalen. Av sikkerhetsmessige årsaker tillates ikke refresh tokens ved implicit flow.

### Eksempel på flyt for en JavaScript/SPA-klient

![SPA](https://cdn.rawgit.com/fia-sikkerhet/fia-sikkerhet.github.com/b4ec6185/images/SPA.svg)

## Authorization code grant

I motsetning til ved implicit flow, overføres tokens ikke via frontkanalen (browseren) med authorization code flow. En autorisasjonskode overføres via frontkanalen inn til klienten, som videre kontakter STS-ens Token-endepunkt vedlagt autorisasjonskoden, og får et identity token, et access token og eventuelt et refresh token i retur. I tillegg må klienten autentisere seg mot STS-en med eksempelvis en delt hemmelighet, eller et klientsertifikat, for å få lov til å bruke autorisasjonskoden til å hente ut informasjon. Dette for å hindre at autorisasjonskoden brukes av uvedkommende tredjepart.

[Klientautentisering](http://openid.net/specs/openid-connect-core-1_0.html#ClientAuthentication) er beskrevet i spesifikasjonen for OpenID Connect Core 1.0.

### Eksempel på flyt for en webapplikasjon med delt hemmelighet med FIA STS

![Webapplikasjon](https://cdn.rawgit.com/fia-sikkerhet/fia-sikkerhet.github.com/b4ec6185/images/Webapplikasjon.svg)

### PKCE (Proof Key for Code Exchange)

I tilfeller der klienten befinner seg i et miljø som gjør at den ikke kan holde på en delt statisk hemmelighet over tid, er PKCE  et alternativ. PKCE-protokollen er spesifisert [her](https://tools.ietf.org/html/rfc7636#section-4).

I korte trekk oppretter klienten en dynamisk hemmelighet, som hashes og vedlegges autentiseringsforespørselen for brukeren. FIA STS må på sin side internt assosiere den hashede hemmeligheten med autorisasjonskoden som utstedes etter autentisering hos den brukervalgte identitetstilbyderen. Når koden senere brukes mot token-endepunktet hos FIA STS, må hemmeligheten, i klartekst, vedlegges forespørselen. FIA STS hasher klarteksthemmeligheten og sammenligner med autorisasjonskodens assosierte hemmelighet.

![PKCE](https://cdn.rawgit.com/fia-sikkerhet/fia-sikkerhet.github.com/146aa8b4/images/PKCE.svg)

#### Eksempel på flyt for en desktop- eller mobilapplikasjon med dynamisk opprettet PKCE-hemmelighet overfor FIA STS

![Desktopapplikasjon](https://cdn.rawgit.com/fia-sikkerhet/fia-sikkerhet.github.com/b4ec6185/images/Desktopapplikasjon.svg)

## Hybrid grant

Hybrid flow kombinerer mulighetene ved implicit og authorization code flow. For de fleste konfigurasjoner vil autorisasjonskode og identity token overføres via frontkanalen, mens access token og eventuelt refresh token hentes via bakkanalen. Det er mulig å også overføre access token via frontkanalen, for spesielle brukstilfeller.

Hybrid flow kan gjerne brukes for serverside-applikasjoner med en delt statisk hemmelighet, og native desktop- eller mobilapplikasjoner sammen med PKCE.

## Client credentials grant

Client credentials er den enkleste granttypen, og brukes for server-til-server-kommunikasjon. Tokens forespørres alltid på vegne av en klient, ikke en bruker.

En klient autentiserer seg mot Token-endepunktet ved hjelp av klientidentifikatoren sin, samt en delt hemmelighet eller klientsertifikat.

### Eksempel på flyt for en systemklient med delt hemmelighet overfor FIA STS

![Systemklient](https://cdn.rawgit.com/fia-sikkerhet/fia-sikkerhet.github.com/ea539872/images/Systemklient.svg)

### Eksempel på flyt for en systemklient med klientsertifikat overfor FIA STS

![Systemklient_klientsertifikat](https://cdn.rawgit.com/fia-sikkerhet/fia-sikkerhet.github.com/ea539872/images/Systemklient_klientsertifikat.svg)

## Resource owner password grant

Ikke relevant for FIA STS siden løsningen ikke eier en brukerbase.

## Extension grants

Extension grants muliggjør å utvide Token-endepunktet med nye (custom) grant types, noe som tillater skreddersøm av samhandlingen mellom klient og STS.

## Refresh tokens

Med refresh tokens oppnår man langvarig tilgang til et tjenestegrensesnitt, siden de tillater en klient å forespørre nye access tokens uten brukerinteraksjon. Det er mulig å nyttiggjøre refresh tokens i hybrid, authorization code eller resource owner password flows, gitt at man har forespurt scopet offline_access.
