Open ID Connect (OIDC) is built on OAuth 2.0. Instead of an Authorisation Server
we have an Identity Provider and return an `id_token` alongside the OAuth
`access_token` which includes claims about the user like name, email,
organisational groups.
