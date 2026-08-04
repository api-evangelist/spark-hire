# Spark Hire (spark-hire)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
