# API Design — Online Coding Judge (Contest Compiler)

## 1. Auth
### POST /api/v1/auth/register
### POST /api/v1/auth/login

## 2. Problems
### GET /api/v1/problems
Returns list of problems

### GET /api/v1/problems/{problemId}
Returns problem details

## 3. Contests
### GET /api/v1/contests
### GET /api/v1/contests/{contestId}
### GET /api/v1/contests/{contestId}/leaderboard

## 4. Runs and Submissions
### POST /api/v1/runs
Run code on sample/custom input

Request:
```json
{
  "problemId": "p101",
  "language": "cpp",
  "code": "...",
  "stdin": "1 2"
}
```

### POST /api/v1/submissions
Submit code for final verdict

### GET /api/v1/submissions/{submissionId}
Fetch status/result

### GET /api/v1/users/{userId}/submissions
Submission history

## 5. Sample Response
```json
{
  "submissionId": "sub_123",
  "status": "QUEUED"
}
```

## 6. Status Codes
- `200 OK`
- `201 Created`
- `400 Bad Request`
- `401 Unauthorized`
- `404 Not Found`
- `429 Too Many Requests`
- `500 Internal Server Error`

## 7. Versioning Strategy
Use URI versioning:
```text
/api/v1/...
```

## 8. Idempotency
- Submission creation can use a client-generated idempotency key
- Prevent duplicate submissions on retry

## 9. Rate Limiting
- Limit run-code API per minute
- Separate stricter limit for submission API during contests
