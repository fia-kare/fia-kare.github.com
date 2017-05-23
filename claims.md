# Claims

| Navn | Eksempelverdi | Beskrivelse |
| --- | --- | --- |
| name | Ola Olsen Nordmann | OIDC spec claim - fullt navn |
| given_name | Ola | OIDC spec claim - fornavn |
| family_name | Nordmann | OIDC spec claim - etternavn |
| middle_name | Olsen | OIDC spec claim - mellomnavn |
| https://nhn.no/claims/identity/pid | 04048900181 | Personidentifikator - typisk norsk fødselsnummer, men med støtte for utenlandske |
| https://nhn.no/claims/identity/security_level | 3 | Definert av "Rammeverk for autentisering og uavviselighet i elektronisk kommunikasjon med og i offentlig sektor". Mulige verdier 2, 3 eller 4. Fastsatt i eller iht. identitetstilbyder |
| https://nhn.no/claims/identity/assurance_level | substantial | Definert av eIDAS. Mulige verdier: low, substantial eller high. Fastsatt i eller iht. identitetstilbyder.  |
| https://nhn.no/claims/hpr/hpr_number | 181000001 | Helsepersonellnummer |
| https://nhn.no/claims/hpr/profession | AU | Verdier iht. NHNs kodeverk |
| https://nhn.no/claims/hpr/authorization | | JSON-struktur iht. NHNs kodeverk |

## https://nhn.no/claims/hpr/authorization

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
