# Online Coding Judge System (System Design Mini Project)

## 📌 Overview

This project focuses on designing an **Online Coding Judge system**, similar to platforms like LeetCode and HackerRank.

The goal was to understand how such systems handle:

* Code execution
* Test case evaluation
* Large number of concurrent submissions
* Scalable and reliable architecture

This design is based on my existing project:

👉 https://github.com/AshutoshYadav08/ContestCompilerMajor

---

## 🎯 Objective

The objective of this mini project is to apply system design concepts like:

* High-Level Design (HLD)
* Low-Level Design (LLD)
* API Design
* Database Design
* Scalability & Reliability

and simulate how a real-world coding platform works internally.

---

## ⚙️ What the system supports

* Users can write and submit code
* Code can be executed with custom input
* Submissions are evaluated against multiple test cases
* System returns verdict like:

  * Accepted
  * Wrong Answer
  * Runtime Error
  * Time Limit Exceeded

---

## 🧠 Key Design Ideas

* **Asynchronous processing** is used for submissions
  (submission → queue → worker → result)

* **Judge0 API** is used for code execution
  (acts as execution engine)

* **Separation of concerns**:

  * API layer handles requests
  * Worker handles execution
  * Database stores submissions and results

* **Scalability approach**:

  * Workers can be scaled horizontally
  * Read-heavy APIs can use caching

---

## 📁 Repository Structure

```
/project-name
├── HLD.md
├── LLD.md
├── api.md
├── scaling.md
└── README.md
```

---

## 📄 What each file contains

* **HLD.md** → overall architecture, components, data flow
* **LLD.md** → classes, DB schema, relationships
* **api.md** → endpoints and request/response formats
* **scaling.md** → scaling strategy, bottlenecks, optimizations

---

## ⚠️ Assumptions

* Code execution is handled by an external service (Judge0)
* Focus is on system design, not full backend implementation
* Basic correctness check (exact output match)

---

## ⚖️ Trade-offs

* Using external execution service reduces complexity
  but limits control over execution environment

* Strong consistency is maintained for submissions
  but some read operations can be eventually consistent

---

## 🚀 Future Improvements

* Build in-house code execution engine (Docker-based sandbox)
* Add real-time contest and leaderboard system
* Improve test case validation (floating point, edge cases)
* Add plagiarism detection
* Optimize for very high submission load

---

## 🙌 Final Note

This project helped me understand how real coding platforms handle:

* concurrent submissions
* distributed execution
* system scalability

and how design decisions affect performance and reliability.

---
