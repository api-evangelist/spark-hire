# Spark Hire (spark-hire)

Spark Hire is a video interviewing and talent assessment platform that lets recruiters screen, interview, and evaluate candidates asynchronously (one-way) and live. The Spark Hire REST API embeds video interviewing into an applicant tracking system or custom hiring app - programmatically managing jobs, interviews, interview questions and reusable question sets, company users (evaluators) and their integration keys, candidate share links, and webhook subscriptions for interview and job lifecycle events.

The API is RESTful with JSON responses served under `https://api.sparkhire.com/v1.0`. Authentication is HTTP Basic: the username is your API key and the password is ignored. Keys are scoped to an individual user and respect that user's permission level.

**Access model:** The API reference at [https://docs.sparkhire.com/](https://docs.sparkhire.com/) is fully public, but API access is **not self-serve** - it must be enabled on your Spark Hire account by Spark Hire before keys will work. Endpoint paths and behavior in this catalog are transcribed from that public reference; the OpenAPI request/response schemas are honestly modeled from the documented resources and were not exercised against a live account (access-gated).

**Rate limit:** 400 requests per minute. A 429 response includes an `X-Rate-Limit-Try-Again-Seconds` header. Prefer webhooks over polling.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/spark-hire/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/spark-hire/refs/heads/main/apis.yml)

## Tags

- Video Interviewing
- Recruiting
- Hiring
- HR Tech
- Talent Assessment
- ATS

## Timestamps

- **Created:** 2026-07-10
- **Modified:** 2026-07-10

## APIs

### Spark Hire Interviews API

Create, list, retrieve, update, and delete one-way and live video interviews - the core artifact a candidate records or attends. Interviews are tied to a job and a candidate, carry a status lifecycle (created, accepted, completed, expired, rescheduled, reset, rated), and can be surfaced to reviewers via basic or advanced share links. Candidate evaluation is captured as interview ratings, exposed through the `InterviewRated` webhook event.

- **Base URL:** `https://api.sparkhire.com/v1.0`
- [Documentation](https://docs.sparkhire.com/)
- [OpenAPI](openapi/spark-hire-openapi.yml)
- [Postman Collection](collections/spark-hire.postman_collection.json)
- [Open Collection](collections/spark-hire.opencollection.json)

### Spark Hire Interview Questions API

Manage the questions a candidate answers within an interview (`/interviews/:uuid/questions`), plus reusable `question_sets` that standardize screening across interviews.

### Spark Hire Jobs API

Create, list, retrieve, update, and delete jobs (requisitions) that interviews are organized under. Jobs emit `JobCreated`, `JobUpdated`, and `JobDeleted` webhook events for keeping an external ATS in sync.

### Spark Hire Users API

Manage the company users who create interviews and evaluate candidates - list, create, get, update, and delete users, and provision or rotate each user's integration API key. Includes `/me` for the authenticated user.

### Spark Hire Webhooks API

Register, list, and delete webhook subscriptions so Spark Hire POSTs changed objects to your server instead of you polling. Events: `InterviewCreated`, `InterviewAccepted`, `InterviewCompleted`, `InterviewDeleted`, `InterviewExpired`, `InterviewRescheduled`, `InterviewReset`, `InterviewRated`, `JobCreated`, `JobUpdated`, `JobDeleted`, with a replay endpoint for missed deliveries.

### Spark Hire Account and Plan API

Read-oriented endpoints for account context - the authenticated user (`/me`), the company plan and its limits (`/plan`), and company details (`/companies/:uuid`).

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/spark-hire)
- [Website](https://www.sparkhire.com)
- [Documentation](https://docs.sparkhire.com/)
- [Plans](plans/spark-hire-plans-pricing.yml)
- [Rate Limits](rate-limits/spark-hire-rate-limits.yml)
- [Fin Ops](finops/spark-hire-finops.yml)

## WebSocket Review

Spark Hire does **not** expose a documented public WebSocket API. Its API is request/response REST over HTTPS plus outbound HTTP webhooks. See [review.yml](review.yml).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
