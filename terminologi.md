# Terminologi

Her gis en kort forklaring på termene som brukes i forbindelse med FIA STS.

## Bruker

En bruker er et menneske som bruker en registrert klient for å få tilgang til ressurser.

## Klient

En klient er programvare som forespør tokens fra FIA STS på to måter:

-	For å autentisere en bruker – hvorpå det vil utstedes et identity token.
-	For å aksessere en ressurs – hvorpå det vil utstedes et access token.

En klient må være registrert og konfigurert i FIA STS.

## Ressurser

En ressurs er noe FIA STS skal beskytte, og STS-en opererer med to typer ressurser:

- Identitetsressurs - for eksempel brukeridentitet
- API-ressurs - et tjenestegrensesnitt

## Claims

Et claim er en påstand om en ressurs, for eksempel e-postadresse eller fødselsnummer.

## Scope

Et scope indikerer hva slags ressurser et token skal få tilgang til. Det være seg et sett med claims eller et tjenestegrensenitt.

Fordi et scope kan bety tilgang til et tjenestegrensesnitt, kan et scope formuleres som en autorisasjon. Det er dog viktig å merke seg at dette da blir en autorisasjon på klientnivå, og ikke for en bruker.

Et token kan inneholde flere scopes. I FIA STS konfigureres et scope som minimum ett underelement av en ressurs, som typisk vil bety grunnleggende tilgang til ressursen. Flere scopes konfigurert for samme ressurs vil bety ulike former for tilgang til samme ressurs.

## Identity token

Et [identity token](http://openid.net/specs/openid-connect-core-1_0.html#IDToken) representerer utfallet av en autentiseringsprosess. Det inneholder minimum et claim kalt sub (subject) – en identifikator for brukeren, og informasjon om når og hvordan brukeren ble autentisert. Token-et kan inneholde ytterligere identitetsdata.

Et identity token er definert i OpenID Connect-spesifikasjonen, og skal være av formatet [JWT](https://tools.ietf.org/html/rfc7519) (JSON Web Token), som er tredelt og består av en header, en payload og en kryptografisk signatur. Denne signaturen vil stamme fra FIA STS' signeringssertifikat.

## Access token, bearer token og reference token

Et [access token](https://tools.ietf.org/html/rfc6749#section-1.4), som også kan være et [bearer token](https://tools.ietf.org/html/rfc6750), representerer den STS-utstedte tilgangen til en beskyttet ressurs.

Et bearer token kan brukes fritt av hvem som måtte være i besittelse av det, og fordrer ikke at en bærer må bevise besittelse av en kryptografisk nøkkel ("proof of possession").

OAuth 2.0-spesifikasjonen stiller ingen formatkrav til access tokens. De kan dermed inneholde en hvilken som helst streng. FIA STS tilbyr to typer access tokens:

-	JWT (JSON Web Token) – også kalt self-contained token – tredelt med header, payload og signatur fra STS-ens signeringssertifikat. Token-et inneholder informasjon om bærende klient og eventuelt en bruker.
-	Reference token – en nøkkel som refererer et token lagret i FIA STS' operasjonelle database, hvis innhold mottakende klient kan hente ved å aksessere introspection-endepunktet vedlagt reference token-et, samt en hemmelig API-nøkkel for klienten.

## Refresh token

Access tokens kan konfigureres til å ha kort levetid, av sikkerhetsmessige årsaker. For å få et nytt access token, kan man bruke et [refresh token](https://tools.ietf.org/html/rfc6749#section-1.5) som har lengre levetid.
