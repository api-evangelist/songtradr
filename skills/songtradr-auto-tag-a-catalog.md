---
name: Auto-tag a music catalog with Songtradr
description: Upload audio files to Songtradr, wait for the AI auto-tagging models to finish, and read back the generated music metadata — tags, genres, musical features and tag strengths.
api: openapi/songtradr-api-openapi.yml
operations: [login, initiateUserFileUpload, userFilesStatus, userFiles, userFile, userFilesSummary]
generated: '2026-08-02'
method: generated
source: openapi/songtradr-api-openapi.yml, conventions/songtradr-conventions.yml
---

# Auto-tag a music catalog with Songtradr

Songtradr's auto-tagging turns an audio file into structured music metadata: a taxonomy of
descriptive tags, genre predictions, musical features and per-tag confidence strengths. The upload
is a two-hop flow — the API hands you a presigned S3 URL and you PUT the audio to S3 yourself.

Base URL: `https://api.songtradr.com`. All operations are under `/api/v1`.

## 1. Authenticate

Call `login` (`POST /api/v1/user/login`) with the account credentials. It returns a `JwtTokenDTO`
whose `token` is a JWT. Send it on every subsequent call as `Authorization: Bearer <token>`.

If you have no account, sign up at https://www.songtradr.com/signup/personal or email
support@songtradr.com for a free API account.

## 2. Start the upload

Call `initiateUserFileUpload` (`POST /api/v1/user/file/{name}/initUpload`), where `{name}` is the
file name you want the object stored under. The body (`FileUploadDTO`) lets you attach
`identifiers` (e.g. ISRC) and `access` configuration. The response (`InitPutRecordingAudioDTO`)
carries a **presigned S3 URL**.

`PUT` the raw audio bytes to that URL directly. That request goes to S3, not to the Songtradr API —
do not send the bearer token with it.

## 3. Poll for processing

Call `userFilesStatus` (`GET /api/v1/user/filesStatus`) until the file reports as processed.
Auto-tagging is asynchronous; there is no webhook and no event stream, so polling is the only
completion signal Songtradr publishes. Back off between polls — the account limit is 120 requests
per minute and exceeding it returns HTTP 429.

## 4. Read the results

- `userFiles` (`GET /api/v1/user/files`) — the paginated list of your files with the derived
  recording metadata. Use `page` (0-based), `size` (default 100) and `sort` (`property,asc|desc`).
  The `FileListDTO` envelope carries `currentPage`, `totalPages` and `totalElements`.
- `userFile` (`GET /api/v1/user/file/{objectKey}`) — a single file by its storage key.
- `userFilesSummary` (`GET /api/v1/user/filesSummary`) — catalog-wide rollups: field summary,
  genre summary, tag summary and musical-features summary. Use this to characterise a whole
  catalog in one call instead of paging every file.

## Rules

- **No idempotency key.** Songtradr documents no `Idempotency-Key` header. Re-issuing
  `initiateUserFileUpload` for the same name creates a new upload intent — track the object key
  yourself rather than blind-retrying.
- **Errors are the Spring Boot envelope**, not RFC 9457: `{timestamp, status, error, message, path}`
  as `application/json`. Branch on the HTTP status; there is no machine-readable error code.
  See `errors/songtradr-problem-types.yml`.
- **Retry 429 and 500** with backoff. Do not retry 400, 401, 403 or 409.
- **401 means the JWT expired** — re-run `login` and retry once.
