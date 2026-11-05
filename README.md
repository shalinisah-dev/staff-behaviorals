# Staff+ Behavioral Interview Toolkit

An open toolkit for turning messy engineering notes into precise, evidence-rich Staff+ behavioral interview stories—in the first pass, without invented facts.

It is designed for candidates interviewing at large technology companies—including MANGOS-style loops—and startups. The framework is company-aware, but not company-dependent: recruiter guidance and the exact interview question always outrank generic coaching heuristics.

## What is included

### Skills

- [`staff-behavioral-coach`](skills/staff-behavioral-coach/SKILL.md): builds and rewrites concise CARL stories, recovers missing evidence, creates follow-up banks, and audits story-bank coverage.
- [`staff-behavioral-reviewer`](skills/staff-behavioral-reviewer/SKILL.md): pressure-tests question fit, ownership, level, technical depth, causality, quality, influence, and durability.

Each skill includes lightweight UI metadata and progressive references for deeper work.

### Templates

- [`evidence-inventory.md`](skills/staff-behavioral-coach/references/evidence-inventory.md): separates facts, attribution, confidence, causality, and gaps before drafting.
- [`story-workbook.md`](skills/staff-behavioral-coach/references/story-workbook.md): creates a speakable 75-120 second CARL plus follow-up preparation.
- [`story-bank-matrix.md`](skills/staff-behavioral-coach/references/story-bank-matrix.md): checks coverage without forcing one strong story into every question.
- [`fast-pass.md`](skills/staff-behavioral-coach/references/fast-pass.md): turns raw notes into an immediate diagnosis, rewrite, and targeted evidence request.
- [`worked-examples.md`](skills/staff-behavioral-coach/references/worked-examples.md): shows how technical, multi-team, and failure answers become Staff+ evidence.

### Evals

The [`evals`](evals) directory contains behavioral cases for fact safety, exact question matching, technical depth, failure ownership, trust repair, AI accountability, fair re-review, and company-rubric humility.

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
3. Write the strongest fact-safe 90-second CARL now—do not wait for perfect inputs.
4. Show what you cut, kept, and still need to add.
5. Ask at most five numbered questions, only if the answers could materially improve the verdict.
6. Create six likely follow-ups with short spoken answers; mark unknowns with specific [fill] notes.
```

Then pressure-test the result:

```text
Use $staff-behavioral-reviewer. Score prompt match, agency, judgment, consequence, and credibility from 0-2. Identify the single biggest weakness, then rewrite only if I ask.
```

The coach should give you a usable draft immediately. It should not respond with generic theory or make you complete a long questionnaire first.

## Install as Codex skills

Clone the repository, then copy or symlink either skill into your Codex skills directory:

```bash
git clone https://github.com/shalinisah-dev/staff-behaviorals.git
mkdir -p ~/.codex/skills
cp -R staff-behaviorals/skills/staff-behavioral-coach ~/.codex/skills/
cp -R staff-behaviorals/skills/staff-behavioral-reviewer ~/.codex/skills/
```

Restart or refresh Codex after installation if the skills do not appear immediately.

## Example prompts

```text
Use $staff-behavioral-coach to turn these notes into a 90-second Staff-level conflict story. Do not invent missing facts.
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

Interview rubrics and formats change. Treat company-specific mappings as dated heuristics unless they come from current official or recruiter-confirmed guidance. The reusable foundation is stable: exact question fit, personal agency, consequential judgment, technical or organizational depth, defensible impact, and honest attribution.

## License

MIT. See [LICENSE](LICENSE).
