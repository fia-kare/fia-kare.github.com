# Tokens

Her gis eksempler på tokens som utstedes av FIA STS.

## id_token

### Et id_token i sin helhet med header.payload.signature:

```
eyJhbGciOiJSUzI1NiIsImtpZCI6IkE4RjcwQTI3QjM1MDdDMDYwREM4Qjg3MUI4REIyNEZFMzBFNTc5QTMiLCJ0eXAiOiJKV1QiLCJ4NXQiOiJxUGNLSjdOUWZBWU55TGh4dU5za19qRGxlYU0ifQ.eyJuYmYiOjE0OTgxMzI5MzYsImV4cCI6MTQ5ODEzMzIzNiwiaXNzIjoiaHR0cHM6Ly9oZWxzZWlkLXN0cy51dHZpa2xpbmcubmhuLm5vIiwiYXVkIjoiTkhOLkZJQS5EZW1vLk12Y0h5YnJpZCIsIm5vbmNlIjoiNjM2MzM3Mjk3MDkyOTY3MDQwLlkySm1PV1kzT1dRdFlqZzRZUzAwT0RRMkxUbGpPREl0TVRjMFpESm1NREUwT0RFNVkyUXhZMlppTXpBdE16Rm1aaTAwTldNMExXSmpNREF0Tm1SbE4yVTNZVFUyTjJNdyIsImlhdCI6MTQ5ODEzMjkzNiwiYXRfaGFzaCI6InJ6S1RCMFJQcnhkQVYyRFBleVR4dFEiLCJzaWQiOiJmNmZkY2Q1NmU0YjRmNjVhYzU2NTViMTcwZjhjMzk5MSIsInN1YiI6ImZ5YXdiMVJuQ3pPcVRwYXFjWWxoNEh0RGxVSk9SRXcycnJvR0l3TmNSMFU9IiwiYXV0aF90aW1lIjoxNDk4MTMyOTM1LCJpZHAiOiJpZHBvcnRlbi1vaWRjIiwibG9jYWxlIjoibmIiLCJodHRwczovL25obi5uby9jbGFpbXMvaWRlbnRpdHkvcGlkIjoiMjQwMTk0OTExMTciLCJodHRwczovL25obi5uby9jbGFpbXMvaWRlbnRpdHkvc2VjdXJpdHlfbGV2ZWwiOiI0IiwiaHR0cHM6Ly9uaG4ubm8vY2xhaW1zL2lkZW50aXR5L2Fzc3VyYW5jZV9sZXZlbCI6ImhpZ2giLCJodHRwczovL25obi5uby9jbGFpbXMvaWRlbnRpdHkvcGlkX3BzZXVkb255bSI6Ii9sZ3JhMGc1Z09TY1YrbFZSMTZYakFVMDc2SEkrK0dtZGJVamJkRm0yOGc9IiwiYW1yIjpbImV4dGVybmFsIl19.qm40yqU8tRyrt53D_VJIPtGk6YM8s2nzP5xO03t4mRvYYm_ePdoEQG5axTOh2JX-TMMYB6gQHLEhygm-KyT3BnL11KuTPg29MNndl_foc4RLA5_3za08jwoHvRF1S4m1C0jD-euF7BRzu8NwT_Y1UT0InlFUtvpOKIj9NalWEPnJYom6OlkN9EzgROAo9seUkbD1YxSxeCHw4_B-o5qZyVnr-hTXaATU-zSB2nEi99UZooIIamKm01F-a1UKdDp-MBv8yJXCqMFmIYm9z-hgjjMf0pAwV8nvAPzzosilVLuE_JGfgPr6Xc4iz4PZObI7TgSqeZYIDfkEByU6JAD_1A
```

### Dekodet payload:

```json
{
  "nbf": 1498132936,
  "exp": 1498133236,
  "iss": "https://helseid-sts.utvikling.nhn.no",
  "aud": "NHN.FIA.Demo.MvcHybrid",
  "nonce": "636337297092967040.Y2JmOWY3OWQtYjg4YS00ODQ2LTljODItMTc0ZDJmMDE0ODE5Y2QxY2ZiMzAtMzFmZi00NWM0LWJjMDAtNmRlN2U3YTU2N2Mw",
  "iat": 1498132936,
  "at_hash": "rzKTB0RPrxdAV2DPeyTxtQ",
  "sid": "f6fdcd56e4b4f65ac5655b170f8c3991",
  "sub": "fyawb1RnCzOqTpaqcYlh4HtDlUJOREw2rroGIwNcR0U=",
  "auth_time": 1498132935,
  "idp": "idporten-oidc",
  "locale": "nb",
  "https://nhn.no/claims/identity/pid": "24019491117",
  "https://nhn.no/claims/identity/security_level": "4",
  "https://nhn.no/claims/identity/assurance_level": "high",
  "https://nhn.no/claims/identity/pid_pseudonym": "/lgra0g5gOScV+lVR16XjAU076HI++GmdbUjbdFm28g=",
  "amr": [
    "external"
  ]
}
```

## access_token

### Et self contained access_token i sin helhet med header.payload.signature:

```
eyJhbGciOiJSUzI1NiIsImtpZCI6IkE4RjcwQTI3QjM1MDdDMDYwREM4Qjg3MUI4REIyNEZFMzBFNTc5QTMiLCJ0eXAiOiJKV1QiLCJ4NXQiOiJxUGNLSjdOUWZBWU55TGh4dU5za19qRGxlYU0ifQ.eyJuYmYiOjE0OTgxMzI5MzYsImV4cCI6MTQ5ODEzNjUzNiwiaXNzIjoiaHR0cHM6Ly9oZWxzZWlkLXN0cy51dHZpa2xpbmcubmhuLm5vIiwiYXVkIjoiaHR0cHM6Ly9oZWxzZWlkLXN0cy51dHZpa2xpbmcubmhuLm5vL3Jlc291cmNlcyIsImNsaWVudF9pZCI6Ik5ITi5GSUEuRGVtby5NdmNIeWJyaWQiLCJzdWIiOiJmeWF3YjFSbkN6T3FUcGFxY1lsaDRIdERsVUpPUkV3MnJyb0dJd05jUjBVPSIsImF1dGhfdGltZSI6MTQ5ODEzMjkzNSwiaWRwIjoiaWRwb3J0ZW4tb2lkYyIsInNjb3BlIjpbInByb2ZpbGUiLCJvcGVuaWQiLCJodHRwczovL25obi5uby9zY29wZXMvaWRlbnRpdHkvcGlkX3BzZXVkb255bSIsImh0dHBzOi8vbmhuLm5vL3Njb3Blcy9pZGVudGl0eS9hc3N1cmFuY2VfbGV2ZWwiLCJodHRwczovL25obi5uby9zY29wZXMvaWRlbnRpdHkvcGlkIiwiaHR0cHM6Ly9uaG4ubm8vc2NvcGVzL2lkZW50aXR5L3NlY3VyaXR5X2xldmVsIl0sImFtciI6WyJleHRlcm5hbCJdfQ.n_iUdjMnRyUJqDtjlGKr7vWhTCitZwFB1RLFeZgIVfUWOAw7hqgcZqwo2Qg1B7AYgrjF49oXgYkGExQcP1dOOCZKiNZ6JYMkLcrMgnhhlb7w1Hb_CyJ-G5dXmB29QkR4tgY33jX0ssDhq8du2YchXRoqrgrPrtp6Mv2SknPRHZ1hw3U-bkvL6F5DSwJJwPeuguHFFjsPkkHvxGt--QWqTPXa-av71wP-bCgoCCXVc0UYVwNvSs-O94v4phPsxGHyrkSRQPMYNLWzI_b5I1sDtrazxgBdQGcGTeQos1to53e6soSJ4fzEy7gu1J9KTff_V_3oTM65_u_UjgeTxzxI2g
```

### Dekodet payload:
```json
{
  "nbf": 1498132936,
  "exp": 1498136536,
  "iss": "https://helseid-sts.utvikling.nhn.no",
  "aud": "https://helseid-sts.utvikling.nhn.no/resources",
  "client_id": "NHN.FIA.Demo.MvcHybrid",
  "sub": "fyawb1RnCzOqTpaqcYlh4HtDlUJOREw2rroGIwNcR0U=",
  "auth_time": 1498132935,
  "idp": "idporten-oidc",
  "scope": [
    "profile",
    "openid",
    "https://nhn.no/scopes/identity/pid_pseudonym",
    "https://nhn.no/scopes/identity/assurance_level",
    "https://nhn.no/scopes/identity/pid",
    "https://nhn.no/scopes/identity/security_level"
  ],
  "amr": [
    "external"
  ]
}
```
