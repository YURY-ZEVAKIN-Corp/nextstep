# Decision Checklist

Use this checklist for every new decision before it is marked `Accepted`.

## 1. Conflict Check

- [ ] Checked for conflicts with existing decisions in the same project.
- [ ] Checked for conflicts with portfolio standards or shared decisions.
- [ ] Checked the project decision register.
- [ ] Checked the portfolio decision register when relevant.
- [ ] If a conflict exists, it is documented explicitly.

## 2. Decision Triage

Assign a triage level based on impact and urgency:

- `Critical`: blocks delivery, security, compliance, or platform direction
- `High`: major architectural or operational impact
- `Medium`: important but localized impact
- `Low`: limited impact and easy to reverse

Checklist:

- [ ] Triage level assigned.
- [ ] Impacted systems, teams, or projects are identified.
- [ ] Reversibility is understood.

## 3. Decision Quality

- [ ] The decision statement is clear.
- [ ] The context explains why the decision is needed.
- [ ] Alternatives were considered.
- [ ] Positive and negative consequences are documented.

## 4. Traceability

- [ ] Related requirements are linked.
- [ ] Related solutions are linked.
- [ ] Related implementation or technology stack artifacts are linked.
- [ ] The decision register is updated or scheduled to be updated.

## 5. Technology Radar Check

- [ ] Major technology choices were checked against the Technology Radar.
- [ ] Radar result is recorded in the solution or technology stack artifact.
- [ ] A non-standard or high-risk choice is justified explicitly.

## Decision Rule

Mark the decision:

- `Pass` if conflict review is complete, triage is assigned, and the decision is traceable and understandable.
- `Fail` if the decision conflicts without resolution, lacks context, or is not traceable.
