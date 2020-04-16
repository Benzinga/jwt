# jwt

**Usage:**

Should be included in HTTP Requests in the `Authorization` header field, or as a query parameter depending on the API documentation for a given endpoint.

```
Authorization: Bearer <jwt-token>
```

**Required Fields:**

Header:
- `alg` (algorithm): Must be string signaling signing algorithm, should be `RS256`
- `typ` (type): Must be `JWT`
- `iss`(issuer): Must be issuer domain such as `sub.domain.tld`
- `kid`(key id): Must be unique signing key identifier string

Payload:
- `sub` (subject): Must be unique user id
- `nbf` (not before): Must be Unix timestamp seconds as `number` to indicate time before which token should not be accepted, typically should be set to creation timestamp.
- `exp` (expires): Must be Unix timestamp seconds as `number`, to indicate time after which token should not be accepted.

Required Fields Example:
```json
Header:
   {
     "alg": "RS256",
     "typ": "JWT",
     "iss":"www.something.tld",
     "kid":"8354bb43-e38c-4c0e-9f4a-b0efa32ef360"
   }
Payload:
   {
     "sub": "15e2f938-0a30-45d0-8fa8-7a23357f06e8",
     "nbf": 1516239022,
     "exp": 1686906796
   }
```

## Helpful Links

- [https://jwt.io/](https://jwt.io/)
