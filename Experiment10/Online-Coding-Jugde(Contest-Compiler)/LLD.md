# LLD — Online Coding Judge (Contest Compiler)

## 1. Core Classes
```text
User
- id
- name
- email
- role

Problem
- id
- title
- difficulty
- statement
- timeLimit
- memoryLimit

Contest
- id
- title
- startTime
- endTime

Submission
- id
- userId
- problemId
- language
- code
- status
- score

TestCase
- id
- problemId
- input
- expectedOutput
- isHidden

JudgeJob
- id
- submissionId
- status
- retryCount
```

## 2. Main Relationships
- One contest has many problems
- One problem has many test cases
- One user has many submissions
- One submission belongs to one user and one problem

## 3. Important Modules
- **Auth Manager**: token validation
- **Submission Manager**: creates runs/submissions
- **Judge Manager**: sends jobs to workers
- **Leaderboard Manager**: computes contest standings

## 4. Sequence Flow — Run Code
```text
User -> Client -> Submission API -> Queue -> Judge Worker -> Execution Engine -> DB -> Client
```

## 5. Sequence Flow — Submit Code
```text
User -> Submission API -> DB(save QUEUED) -> Queue -> Judge Worker
-> Hidden Test Cases -> Final Verdict -> DB -> Leaderboard Update
```

## 6. Database Schema
### users
- id (PK)
- name
- email
- password_hash
- role

### problems
- id (PK)
- title
- slug
- difficulty
- statement
- time_limit_ms
- memory_limit_mb

### contests
- id (PK)
- title
- start_time
- end_time

### contest_problems
- contest_id
- problem_id

### submissions
- id (PK)
- user_id
- problem_id
- contest_id
- language
- source_code
- status
- runtime_ms
- memory_kb
- created_at

### test_cases
- id (PK)
- problem_id
- input_data
- expected_output
- is_hidden

## 7. Indexing
- `submissions(user_id, created_at)`
- `submissions(problem_id, status)`
- `problems(slug)`
- `contest_problems(contest_id, problem_id)`

## 8. Design Patterns Used
- **Factory Pattern**: create language-specific executors
- **Strategy Pattern**: verdict evaluation per language/problem type
- **Singleton**: config/connection manager
