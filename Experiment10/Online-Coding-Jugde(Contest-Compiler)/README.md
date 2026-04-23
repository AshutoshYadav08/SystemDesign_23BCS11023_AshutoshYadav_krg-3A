# Contest Compiler — System Design Mini Project

## Project Overview
This project designs an **Online Coding Judge** inspired by LeetCode/HackerRank and based on my **Contest Compiler** project. The system supports problem solving, code execution, submission judging, contests, and leaderboards.

## Included Files
- `HLD.md`
- `LLD.md`
- `api.md`
- `scaling.md`

## Assumptions
- Code execution happens in a secure sandbox/external judge
- Hidden test cases are not exposed to users
- Contests may receive traffic spikes near start/end times

## Tech Stack (Suggested)
- **Frontend:** Next.js
- **Backend:** Node.js / Express
- **DB:** PostgreSQL or MongoDB
- **Cache:** Redis
- **Queue:** Kafka / RabbitMQ
- **Execution Engine:** Judge0 or custom sandbox workers

## Design Trade-offs
- Async judging improves scale but adds small verdict delay
- Cached leaderboard improves speed but may be slightly stale
- Separate judge workers improve isolation and reliability

## Future Improvements
- WebSocket-based live verdict updates
- Plagiarism detection
- Multi-language custom test runners
- Better analytics for contests
