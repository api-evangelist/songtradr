---
name: Manage a Songtradr account and API access
description: Obtain and refresh Songtradr bearer JWTs, read and update the authenticated profile, and run the password reset and sign-up flows.
api: openapi/songtradr-api-openapi.yml
operations: [login, token, me, editMe, signUp, forgotPassword, updatePassword, deleteUserFile]
generated: '2026-08-02'
method: generated
source: openapi/songtradr-api-openapi.yml, authentication/songtradr-authentication.yml
---

# Manage a Songtradr account and API access

Songtradr uses a plain bearer-JWT model — no OAuth, no scopes, no API keys. Everything an agent can
do is bounded by the single account the JWT was issued for.

Base URL: `https://api.songtradr.com`. All operations are under `/api/v1`.

## Getting a token

- `login` (`POST /api/v1/user/login`) — send `LoginDTO` credentials, receive `JwtTokenDTO`. The
  `token` field is the JWT. Use it as `Authorization: Bearer <token>`.
- `token` (`POST /api/v1/user/token`) — issues a bearer JWT from a `TokenRequest`.

The API publishes no token lifetime and no refresh endpoint. Treat a `401 Unauthorized` on any call
as "the token expired": re-run `login` once and retry the original request.

## Profile

- `me` (`GET /api/v1/user/me`) — read the authenticated `UserDTO`.
- `editMe` (`POST /api/v1/user/me`) — update it with a `SaveUserDTO`. This is a **full-DTO POST**,
  not a JSON Patch — read with `me` first, mutate the fields you intend to change, and send the
  whole object back, or you will blank fields you omitted.

## Account lifecycle

- `signUp` (`POST /api/v1/user/sign-up`) — create an account from a `SignUpDTO`. Returns `403` if
  the caller is not permitted to sign up other users, and `409` if the identity is already taken.
- `forgotPassword` (`POST /api/v1/user/forgot-password`) — triggers a reset email for a
  `ForgotPasswordDTO`.
- `updatePassword` (`POST /api/v1/user/update-password`) — change the password with an
  `UpdatePasswordDTO`. Returns `204 No Content` on success.

## Destructive operations — require confirmation

- `updatePassword` changes the credential the account authenticates with. An agent must have
  explicit human confirmation before calling it; a failed or unintended call locks the account out.
- `deleteUserFile` (`DELETE /api/v1/user/file/{objectKey}`) permanently removes an uploaded file
  and its derived tagging. There is no undelete and no soft-delete flag. Confirm the object key
  against `userFiles` before deleting, and never delete from a wildcard match.

See `agentic-access/songtradr-agentic-access.yml` for the per-operation execution contract.

## Rules

- **No scopes.** A Songtradr JWT is all-or-nothing for its account. There is no way to mint a
  read-only credential, so an agent holding a token holds write and delete authority too — scope it
  by putting the agent on a dedicated account rather than by the token.
- **No idempotency key.** Do not blind-retry `signUp`, `token` or `updatePassword`.
- **Errors** are `{timestamp, status, error, message, path}` JSON. `400` validation, `401` bad or
  expired token, `403` not permitted, `409` identity taken, `429` rate limited, `500` server error.
