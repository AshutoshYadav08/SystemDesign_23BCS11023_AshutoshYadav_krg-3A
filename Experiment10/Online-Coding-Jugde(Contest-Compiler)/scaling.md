# Scaling & Reliability — Online Coding Judge (Contest Compiler)

## 1. Load Balancing
- Use load balancer before API servers
- Distribute traffic across stateless backend instances

## 2. Horizontal vs Vertical Scaling
- **Horizontal**: API servers and judge workers
- **Vertical**: temporary increase for DB or cache when required
- Prefer horizontal scaling for contest spikes

## 3. Caching Strategy
- Cache problem metadata
- Cache contest info and leaderboard snapshots
- Use CDN/object storage for assets and statements

## 4. Database Scaling
- Read replicas for heavy reads
- Partition submissions by contest or time for large scale
- Archive old submissions

## 5. Failure Handling
- Retry failed judge jobs
- Use dead-letter queue for repeated failures
- Circuit breaker around external code execution service

## 6. Main Bottleneck
**Judge execution throughput** during peak contests.

**Optimization:** async queue + autoscaled workers + lightweight polling/websocket status updates.

## 7. Reliability Notes
- Store submission before sending to queue
- Use durable queue
- Make judge result update idempotent
