# Worked Synthetic Examples

These examples are invented and demonstrate transformations, not scripts to memorize.

## 1. Technical problem: replace outcome-only language with mechanism

### Weak input

> I led a performance initiative and improved startup by 18%. I coordinated with several teams and ran an experiment to prove impact.

### Diagnosis

- The metric proves consequence, not technical depth.
- “Led” and “coordinated” hide the candidate's decision.
- No symptom, root cause, correctness risk, or validation mechanism appears.

### Stronger shape

> Our startup trace showed a derived-data reconciliation job repeatedly blocking the UI thread. The obvious fix—moving the entire job to a background queue—could expose partially updated state to later startup work. I separated read-only analysis from the state transition, moved the safe portion off the critical path, and kept the ordered write behind an explicit completion boundary. We validated both startup latency and data consistency before rollout. The change improved startup by 18%, and the boundary became the pattern for two related workflows.

Why it works: the answer now contains a failure mode, diagnosis, consequential change, safety boundary, validation, and leverage.

## 2. Multi-team influence: replace attendance with changed behavior

### Weak input

> I aligned Client, Platform, Security, and Product through weekly meetings and a shared document. We launched on time.

### Diagnosis

- The teams are named, but their competing constraints are not.
- Meetings and documents are activities, not influence.
- “On time” does not reveal the candidate's judgment.

### Stronger shape

> Client wanted a local design to protect schedule; Security required one authoritative policy state; Platform could staff only a narrow server change; and Product would not remove offline recovery. I put the four constraints and two viable architectures into one decision record, built a small proof for the disputed recovery path, and used it to show that a server-authoritative design met the security requirement with less duplicated client state. Client accepted an asynchronous UI, Platform staffed the narrow API, and Security approved the boundary. We launched with one source of truth and reused the decision model for the next cross-platform feature.

Why it works: each team changes a decision, and the shared artifact supports a consequential choice rather than standing in for it.

## 3. Failure: preserve the mistake instead of polishing it away

### Weak input

> I joined a team with low morale, introduced agile, and later reorganized the work into two streams. The product succeeded and I learned to listen.

### Diagnosis

- The candidate's mistake and harm are vague.
- Recovery dominates the failure.
- “Learned to listen” has no later behavioral proof.

### Stronger shape

> I misdiagnosed a trust problem as an execution problem and imposed a sprint process before understanding the team. Over six weeks, retrospectives became blame sessions and demo preparation consumed more engineering time. After partners and engineers challenged the approach, I told leadership the process was worsening the situation and removed it. I held listening sessions, replaced performance-heavy demos with short written risk updates, and separated exploratory work from committed delivery. Morale and predictability recovered. On my next team, I spent the first month mapping goals and relationships before proposing any operating change; that became my standard entry plan.

Why it works: the failure, harm, accountability, repair, and later proof are all visible.
