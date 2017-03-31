## FIA STS

FIA står for Felles Infrastruktur og Arkitektur, og FIA Sikkerhets oppgave er å tilby en løsning som tillater formidling av identitet på kryss av organisasjoner i helsesektoren.

STS står for Security Token Service, og er en sentralisert formidler av identitet fra ulike identitetstilbydere, i tillegg til å kunne utstede tokens på vegne av konfigurerte ressurser.

Hensikten med en STS er å outsource sikkerhetsfunksjonalitet til en sentralisert tjeneste, slik at man kan unngå duplisering av funksjonaliteten på tvers av tjenestegrensesnitt, web-, skrivebords- og mobilapplikasjoner.
FIA STS behersker protokoller som [OpenID Connect 1.0](http://openid.net/specs/openid-connect-core-1_0.html) og [OAuth 2.0](https://tools.ietf.org/html/rfc6749), i tillegg til en eldre protokoll som [WS-Federation](http://docs.oasis-open.org/wsfed/federation/v1.2/ws-federation.html).

![sts-modell](https://raw.githubusercontent.com/fia-kare/fia-kare.github.com/master/images/sts_model.png)

Modellen viser en forenklet flyt for autentisering og API-tilgang, etter hvilket mønster FIA STS-en er designet.
FIAs STS er en RP-STS (Relying Party) hvilket vil si at tjenesten ikke autentiserer klientene selv, men baserer seg på tokens basert på ovennevnte sikkerhetsprotokoller, utstedt fra IP-STS-er (Identity Provider) som er konfigurert som identitetstilbydere i FIA STS.

- [Terminologi](terminologi.md)

- [Claims](claims.md)

- [Klientregistrering](dcr.md)

- [Autentiseringsflyt og grant types](autentiseringsflyt_grant_types.md)

- [Endepunkter](endepunkter.md)

- [Implementerte spesifikasjoner](implementerte_spesifikasjoner.md)

- [Klientbiblioteker](http://openid.net/developers/libraries/) - Ekstern lenke til openid.net
