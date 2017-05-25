# Claims

| Navn | Eksempelverdi | Beskrivelse |
| --- | --- | --- |
| at_hash | y9WtN9oBLG9q0J6NDbAHZQ | OIDC Access Token hash value |
| amr | [ "external" ] | OIDC - Authentication Methods References - anvendte autentiseringsmetoder |
| aud | kjernejournal | JWT Audience - hvem tokenet er tiltenkt |
| auth_time | 1495545039| OIDC - når sluttbruker-autentiseringen fant sted |
| client_id | `https://dips.no/arena` | Identifiserer applikasjonen |
| exp | 1495545339 | JWT Expiration Time |
| iat | 1495545039 | JWT Issued At |
| idp | `https://idporten.difi.no` | Identity Provider - identitetstilbyderen brukeren autentiserte seg hos |
| iss | `https://helseid-sts.utvikling.nhn.no` | JWT Issuer |
| jti | ce49934e518a8197a5baff11d8d3f908 | JWT ID - unik for tokenet |
| nbf | 1495545039 | JWT Not before |
| nonce | e7bfdd93b9474457a0bf13976c3b30ef | OIDC - random verdi som brukes mot replay-angrep |
| scope | [ "openid", "profile" ] | Hva slags formål tokenet har |
| sid | | Session ID - brukes av FIA STS |
| sub | | JWT Subject - Unikt for en gitt bruker for en gitt klient. Hash-verdi av client_id + pid + salt |
| name | Ola Olsen Nordmann | OIDC spec claim - fullt navn |
| given_name | Ola | OIDC spec claim - fornavn |
| family_name | Nordmann | OIDC spec claim - etternavn |
| middle_name | Olsen | OIDC spec claim - mellomnavn |
| `https://nhn.no/claims/client/organization_number` | 994598759 | Klientens organisasjonsnummer |
| `https://nhn.no/claims/hpr/authorization` | | JSON-struktur iht. NHNs kodeverk |
| `https://nhn.no/claims/hpr/hpr_number` | 181000001 | Helsepersonellnummer |
| `https://nhn.no/claims/identity/assurance_level` | substantial | Definert av eIDAS. Mulige verdier: low, substantial eller high. Fastsatt i eller iht. identitetstilbyder. Vil antagelig erstatte security_level på sikt. |
| `https://nhn.no/claims/identity/pid` | 04048900181 | Personidentifikator - typisk norsk fødselsnummer, men med støtte for utenlandske |
| `https://nhn.no/claims/identity/pid_pseudonym` | /lgra0g5gOScV+lVR16XjAU076HI++GmdbUjbdFm28g= | Personidentifikator - pseudonymisert vha. HMAC |
| `https://nhn.no/claims/identity/security_level` | 3 | Definert av "Rammeverk for autentisering og uavviselighet i elektronisk kommunikasjon med og i offentlig sektor". Mulige verdier: 2, 3 eller 4. Fastsatt i eller iht. identitetstilbyder |


## `https://nhn.no/claims/hpr/authorization`

```json
{
  "profession": "LE",
  "authorization": {
    "value": "1",
    "description": "Autorisasjon"
  },
  "requisition_rights": [
    {
  	"value": "1",
  	"description": "Full rekvisisjonsrett"
    }
  ],
  "specialities": [
    {
  	"Value": "1",
  	"Description": "Allmennmedisin"
    }
  ]
}
```
