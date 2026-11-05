# Technical and AI Depth

## Technical kernel

Every technical leadership story needs a compact mechanism:

1. **Constraint or failure mode:** What could not be solved by the obvious approach?
2. **Evidence and diagnosis:** What observation narrowed the search and established the root cause?
3. **Consequential change:** What code, data model, protocol, architecture, or operating boundary changed?
4. **Correctness boundary:** What ordering, concurrency, privacy, security, migration, or recovery risk had to remain safe?
5. **Validation:** What proved the change worked and did not create a regression?

Use plain language before internal terminology. A technically sophisticated outsider should understand both the problem and the solution.

## Architecture versus investigation

Architecture stories show how the candidate reasoned across constraints and designed a system. Investigation stories show how the candidate moved from a symptom through evidence to a root cause and verified fix. Both can be Staff+; they answer different prompts.

## Performance stories

Moving work off a critical thread is not merely scheduling it elsewhere. Explain:

- which work was order-dependent;
- which state could be observed concurrently;
- what could be deferred safely;
- persistence and recovery behavior;
- how correctness and user experience were validated.

An experiment may prove user impact. It does not substitute for the diagnosis and safe implementation.

## Reliability and incidents

Separate immediate containment, root cause, durable repair, and prevention. Strong stories expose the invariant that was violated and the mechanism that now detects or repairs future divergence.

## AI-driven work

Treat AI as an engineering component with an accountability boundary.

Require:

- **Work:** the meaningful task AI performed and why it fit;
- **Human judgment:** architecture, decomposition, acceptance criteria, or decisions retained by the candidate;
- **Trust:** tests, review, privacy, security, and correctness checks;
- **Iteration:** incorrect output or workflow limitations and what changed after observing them;
- **Attributable advantage:** speed, scope, quality, exploration, or accessibility compared with the prior approach;
- **Consequence:** a user, business, quality, or organizational result;
- **Scaling:** reusable workflow, tooling, teaching, or adoption beyond a one-off personal use when claimed.

Do not use code-generation percentages as impact. Do not invent a control group or counterfactual. If the work was personal experimentation, label it honestly and use it for continuous-learning evidence rather than enterprise impact.
