# Staff+ Behavioral Interview Toolkit

An open toolkit for turning messy engineering notes into precise, evidence-rich Staff+ behavioral interview stories—in the first pass, without invented facts.

It is designed for candidates interviewing at large technology companies—including MANGOS-style loops—and startups. The framework is company-aware, but not company-dependent: recruiter guidance and the exact interview question always outrank generic coaching heuristics.

## See it work end to end

This transcript is synthetic. Every detail in the rewrite comes from the notes below; the missing production result stays visibly missing.

### Candidate input

> **Question:** Tell me about a complex technical problem you solved.
>
> **Rough notes:** Customers sometimes received duplicate billing reminders after retries. An API queued the reminder, then a worker wrote it to the database and acknowledged the job. I added correlation IDs and found the same job was replayed when the worker crashed after the database commit but before acknowledgment. Acknowledging first could silently lose reminders. I implemented an idempotency key from the account and billing event, enforced it with a database uniqueness constraint, treated duplicate inserts as already applied, and acknowledged only after commit. We added crash-injection tests around the boundary and rolled it out gradually. I owned the diagnosis and core implementation. I do not have the production incident-rate result handy.

### Coach output

**Verdict: This directly answers technical investigation. It is strong on diagnosis and correctness; the missing production result limits the impact claim, not the technical claim.**

**Target thesis:** I traced duplicate customer notifications to a crash-consistency gap and made the user-visible effect idempotent without creating a message-loss window.

- **Cut:** none; the notes are already relevant to the technical prompt.
- **Keep:** the reproduced crash window, rejected acknowledge-first alternative, idempotency mechanism, and crash-injection tests.
- **Add:** a verified post-rollout production signal and evidence of reuse, if either exists.

**CARL**

> Customers were occasionally receiving duplicate billing reminders after retries, which was both confusing and trust-eroding. I owned the investigation and core fix.
>
> **First,** I added correlation IDs across the API and worker path. That showed the same job was replayed when the worker committed the reminder to the database but crashed before acknowledging the queue item.
>
> **Second,** I rejected the tempting fix of acknowledging first, because a crash between acknowledgment and the database write would silently lose the reminder. Instead, I derived an idempotency key from the account and billing event, enforced it with a database uniqueness constraint, and treated a duplicate insert as an already-completed effect.
>
> **Third,** I kept acknowledgment after commit and added crash-injection tests around that boundary before a gradual rollout.
>
> The change made retries safe for the failure window we reproduced: they could no longer create a second reminder, while uncommitted work remained retryable. `[fill: verified production duplicate-rate, support-ticket, or incident result]`
>
> My takeaway was to reason separately about delivery and user-visible effects: queues may redeliver, so correctness has to live at the state transition, not in an assumption of exactly-once execution.

**Evidence boundaries**

- Demonstrated: failure mechanism, rejected alternative, implemented boundary, crash-injection validation, gradual rollout.
- Missing: measured production reduction and whether the pattern became a broader standard.
- Do not claim: zero duplicates globally, lower support volume, or organization-wide adoption without evidence.

**Three verdict-changing questions**

1. What production signal confirmed duplicate reminders declined after rollout?
2. Did the idempotency pattern become required or reused for other retryable jobs?
3. What was the rollout safeguard or rollback trigger?

That is the intended experience: a usable answer now, exact evidence boundaries, and only questions that could materially strengthen it.

## What is included

### Skills

- [`staff-behavioral-coach`](skills/staff-behavioral-coach/SKILL.md): builds and rewrites concise CARL stories, recovers missing evidence, creates follow-up banks, and audits story-bank coverage.
- [`staff-behavioral-reviewer`](skills/staff-behavioral-reviewer/SKILL.md): pressure-tests question fit, ownership, level, technical depth, causality, quality, influence, and durability.

Each skill includes lightweight UI metadata and progressive references for deeper work.

### Templates

- [`evidence-inventory.md`](skills/staff-behavioral-coach/references/evidence-inventory.md): separates facts, attribution, confidence, causality, and gaps before drafting.
- [`story-workbook.md`](skills/staff-behavioral-coach/references/story-workbook.md): creates a speakable answer targeting about 90 seconds, within a 75-120 second range, plus follow-up preparation.
- [`story-bank-matrix.md`](skills/staff-behavioral-coach/references/story-bank-matrix.md): checks coverage without forcing one strong story into every question.
- [`fast-pass.md`](skills/staff-behavioral-coach/references/fast-pass.md): turns raw notes into an immediate diagnosis, rewrite, and targeted evidence request.
- [`worked-examples.md`](skills/staff-behavioral-coach/references/worked-examples.md): shows how technical, multi-team, and failure answers become Staff+ evidence.

### Evals

The [`evals`](evals) directory contains portable behavior specifications for fact safety, exact question matching, technical depth, failure ownership, trust repair, AI accountability, fair re-review, and company-rubric humility. They define required and forbidden behavior; they are not an executable model-evaluation harness. See [`evals/README.md`](evals/README.md).

## Core idea

Staff+ interviewing is not a contest to tell the largest project story. It is an evidence problem:

> **Problem worth solving -> judgment exercised -> people or systems changed -> measurable consequence**

The strongest answer is the smallest truthful narrative that proves the exact competency requested.

## Get a useful result in five minutes

Paste one interview question and your rough notes, then use:

```text
Use $staff-behavioral-coach in fast-pass mode.

1. Name the exact signal this question tests.
2. Tell me whether this example actually proves it.
3. Write the strongest fact-safe CARL now, targeting about 90 seconds within a 75-120 second range—do not wait for perfect inputs.
4. Show what you cut, kept, and still need to add.
5. Ask at most five numbered questions, only if the answers could materially improve the verdict.
6. Create six likely follow-ups with short spoken answers; mark unknowns with specific [fill] notes.
```

Then pressure-test the result:

```text
Use $staff-behavioral-reviewer. Score prompt match, agency, judgment, consequence, and credibility from 0-2. Identify the single biggest weakness, then rewrite only if I ask.
```

The coach should give you a usable draft immediately. It should not respond with generic theory or make you complete a long questionnaire first.

## Install

### Codex

Clone the repository, then copy or symlink either skill into your Codex skills directory:

```bash
git clone https://github.com/shalinisah-dev/staff-behaviorals.git
mkdir -p ~/.codex/skills
cp -R staff-behaviorals/skills/staff-behavioral-coach ~/.codex/skills/
cp -R staff-behaviorals/skills/staff-behavioral-reviewer ~/.codex/skills/
```

Restart or refresh Codex after installation if the skills do not appear immediately.

Invoke them as `$staff-behavioral-coach` and `$staff-behavioral-reviewer`.

### Claude Code

Claude Code uses the same `SKILL.md` structure. Copy the folders into your personal skills directory:

```bash
mkdir -p ~/.claude/skills
cp -R staff-behaviorals/skills/staff-behavioral-coach ~/.claude/skills/
cp -R staff-behaviorals/skills/staff-behavioral-reviewer ~/.claude/skills/
```

Invoke them as `/staff-behavioral-coach` and `/staff-behavioral-reviewer`. See Anthropic's [Claude Code skills documentation](https://code.claude.com/docs/en/skills).

### Claude app

Package either skill folder as a ZIP, then upload it from **Customize → Skills → + → Create skill → Upload a skill**:

```bash
cd staff-behaviorals/skills
zip -r ../staff-behavioral-coach.zip staff-behavioral-coach
zip -r ../staff-behavioral-reviewer.zip staff-behavioral-reviewer
```

See Anthropic's [custom-skill upload instructions](https://support.claude.com/en/articles/12512180-use-skills-in-claude).

## Example prompts

```text
Use $staff-behavioral-coach to turn these notes into a Staff-level conflict story of about 90 seconds. Do not invent missing facts.
```

```text
Use $staff-behavioral-reviewer to pressure-test this answer for a complex technical investigation prompt.
```

```text
Audit my story bank for strategic leadership, technical depth, multi-team influence, failure, people development, quality, and AI-driven impact.
```

## Recommended workflow

1. Start with the evidence inventory before polishing language.
2. Identify the exact competency the question requires.
3. Choose one thesis and write a concise first-pass answer.
4. Preserve technical detail and secondary evidence in a follow-up bank.
5. Run the adversarial reviewer.
6. Correct only genuine evidence gaps; do not add impressive-sounding claims.

## Privacy and provenance

This public repository intentionally contains no private interview stories, employer-confidential implementation details, personal metrics, mock-interviewer correspondence, or third-party coaching material. The worked examples are synthetic, concrete, and non-personal.

Before publishing your own story bank:

- generalize internal names and sensitive system details;
- remove personal data and confidential metrics;
- distinguish recollection from verified artifacts;
- never invent facts to fill a stronger narrative.

## Company calibration

Interview rubrics and formats change. Treat company-specific mappings as dated heuristics unless they come from current official or recruiter-confirmed guidance. The [calibration reference](skills/staff-behavioral-coach/references/level-and-company-calibration.md) gives concrete answer-shaping lenses for high-scale product and infrastructure roles, principles-heavy loops, AI labs, and startups. It changes the headline, selected tradeoff, and result ordering—not the facts.

## License

MIT. See [LICENSE](LICENSE).
