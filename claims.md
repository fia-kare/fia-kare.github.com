# Claims

| Navn | Kortnavn | Eksempelverdi | Beskrivelse |
| --- | --- | --- | --- |
| http://nhn.no/identity/claims/nnin | identity/nnin | 04048900181 | Norwegian national identification number - fødselsnummer |
| http://nhn.no/identity/claims/lastname | identity/last_name | Nordmann | |
| http://nhn.no/identity/claims/firstname | identity/first_name | Ola | |
| http://nhn.no/identity/claims/middlename | identity/middle_name | Olsen | |
| http://nhn.no/identity/claims/securitylevel | identity/security_level | 3 | Definert i eller iht. identitetstilbyder |
| http://nhn.no/hpr/claims/hprnumber | hpr/hpr_number | 181000001 | |
| http://nhn.no/hpr/claims/profession | hpr/profession | AU | Verdier iht. NHNs kodeverk |
| http://nhn.no/hpr/claims/authorization | hpr/authorization | | JSON-struktur iht. NHNs kodeverk |

## authorization

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
