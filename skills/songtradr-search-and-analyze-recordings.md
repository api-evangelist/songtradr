---
name: Search and analyze recordings with Songtradr
description: Search a Songtradr catalog with semantic music filters, then pull deep per-recording metadata — tag strengths, time-localised taggrams, genre predictions and similarity vectors.
api: openapi/songtradr-api-openapi.yml
operations: [login, allowedMusicalFeatures, userFiles, recordingsMediumByIds, recordingsByIdsWithTagstrengths, recordingsByIdsWithTaggrams, recordingsByFolderWithTagstrengths, getSimilarityVector]
generated: '2026-08-02'
method: generated
source: openapi/songtradr-api-openapi.yml, conventions/songtradr-conventions.yml
---

# Search and analyze recordings with Songtradr

Songtradr exposes music semantics as filters and as scored model outputs. This skill covers finding
recordings and then reading the deep metadata attached to them.

Base URL: `https://api.songtradr.com`. All operations are under `/api/v1`.

## 1. Authenticate

Call `login` (`POST /api/v1/user/login`) and use the returned `jwtToken` as
`Authorization: Bearer <token>` on every call.

## 2. Learn the filter vocabulary before you filter

Call `allowedMusicalFeatures` (`GET /api/v1/allowedValues/musicalFeatures`) first. It returns
`SearchFilterValuesDTO` — the enumerated allowed values for every musical-feature search filter.
Never guess a filter value; a value outside the published set will not match.

## 3. Search

Call `userFiles` (`GET /api/v1/user/files`) with the musical-feature filters plus `ISRC` for an
exact-identifier lookup. Paginate with `page` / `size` / `sort`; the default sort is
`uploadStartTime,DESC`.

## 4. Pull deep metadata by id

All three operations take a comma-joined list in the `{ids}` path segment and return an
unpaginated array — keep batches modest so you stay under the 120 requests-per-minute limit.

- `recordingsMediumByIds` (`GET /api/v1/user/recording/{ids}`) — medium-detail recordings:
  titles, tracks, contributor parties, genres, tags and musical features.
- `recordingsByIdsWithTagstrengths` (`GET /api/v1/user/recording/{ids}/tagstrengths`) — the same
  recordings with a **confidence score per tag**. Use this when you need to threshold tags rather
  than take them as booleans.
- `recordingsByIdsWithTaggrams` (`GET /api/v1/user/recording/{ids}/taggrams`) — **time-localised**
  tags, i.e. where in the recording each tag fires. Use this for scene/segment-level matching.

For a whole folder at once, call `recordingsByFolderWithTagstrengths`
(`GET /api/v1/user/folder/{folderName}/tagstrengths`).

## 5. Find similar music

Call `getSimilarityVector` (`GET /api/v1/similarityVectors/{isrcOrTrackId}`). The path segment
accepts **either** an ISRC **or** a Songtradr track GUID. It returns `SimilarityVectorDto` — the
embedding you compare against other recordings' vectors to rank similarity yourself. Songtradr does
not expose a "find similar tracks" endpoint; you do the nearest-neighbour step.

## Rules

- **Reference data first.** `allowedMusicalFeatures` is the source of truth for filter values.
- **Two identifier systems.** ISRC is the cross-catalog key; `songtradrTrackGuid` is Songtradr's
  own. `getSimilarityVector` accepts both; treat them as interchangeable inputs, not equal outputs.
- **Rate limit 120/min per account**, signalled only by HTTP 429 — there are no `RateLimit-*`
  response headers to read ahead. See `rate-limits/songtradr-rate-limits.yml`.
- **Errors** are `{timestamp, status, error, message, path}` JSON, not RFC 9457. Retry 429 and 500
  with backoff; re-`login` on 401.
