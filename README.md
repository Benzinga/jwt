# jwt

**Usage:**

Should be included in HTTP Requests in the `Authorization` header field, or as a query parameter depending on the API documentation for a given endpoint.

For JWT, we recommend using RS256. You may generate a sample JWT using https://jwt.io/. You need to send us public/private key depending upon which algorithm you are using. We will add that public/private key on our side, so it will verify signature generated. Also, you need to send us the value of <b>iss</b> (issuer) value of payload. <br/> <b>Note:</b> Prepend <b>Bearer</b> to your actual jwt when you authorize here to test.

```
Authorization: Bearer <jwt-token>
```

**Required Fields:**

Header:
- `alg` (algorithm): Must be string signaling signing algorithm, should be `RS256`
- `typ` (type): Must be `JWT`

Payload:
- `iss`(issuer): Must be issuer domain such as `sub.domain.tld`
- `kid`(key id): Must be unique signing key identifier string
- `sub` (subject): Must be unique user id
- `nbf` (not before): Must be Unix timestamp seconds as `number` to indicate time before which token should not be accepted, typically should be set to creation timestamp.
- `exp` (expires): Must be Unix timestamp seconds as `number`, to indicate time after which token should not be accepted.

Required Fields Example:
```json
Header:
   {
     "alg": "RS256",
     "typ": "JWT"
   }
Payload:
   {
     "iss":"www.something.tld",
     "kid":"8354bb43-e38c-4c0e-9f4a-b0efa32ef360",
     "sub": "15e2f938-0a30-45d0-8fa8-7a23357f06e8",
     "nbf": 1516239022,
     "exp": 1686906796
   }
```

## Helpful Links
- [https://auth0.com/blog/navigating-rs256-and-jwks/](https://auth0.com/blog/navigating-rs256-and-jwks/)
- [https://jwt.io/](https://jwt.io/)
- [https://stackoverflow.com/questions/39239051/rs256-vs-hs256-whats-the-difference](https://stackoverflow.com/questions/39239051/rs256-vs-hs256-whats-the-difference)
