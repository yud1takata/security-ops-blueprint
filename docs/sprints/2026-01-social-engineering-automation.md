# Sprint Plan: Automated Social Engineering Postures (2026-01)

## Purpose
Automate lab-only social engineering posture tests to drive detection engineering and purple-team validation.

WARNING: Lab-only. Do not run in real environments.

## Preconditions
- Backlog item BL-036 exists in `docs/backlog.md`.
- Posture list exists in `docs/social-engineering-postures.md`.
- Posture playbooks live under `ansible/postures/social_engineering/`.

## Scope
- Implement apply/revert automation for all posture tests.
- Add WARNING banners, lab-only safeguards, and rollback guidance.
- Define expected signals and validation steps per posture.
- Capture validation evidence in `docs/logs/`.
- Ensure portability via variables (no hard-coded hosts).

## Out of scope
- Any changes that weaken real environments.
- Non-reversible posture changes.

## Milestones
- M1 Posture coverage mapping and owners (Day 1)
- M2 Playbook automation + docs (Days 2-4)
- M3 Validation evidence captured (Day 5)

## Work items (Backlog)
- BL-036: Automated social engineering postures (lab-only)

## Agent assignments
- PM: scope lock, warnings, and risk acceptance log.
- Builder: posture playbooks, vars, and revert paths.
- Analyst: validation and evidence capture.

## Purple team breakdown
- Red: define pretexts and expected attacker reliance.
- Blue: map detections and alerting thresholds.
- Purple: coordinate run order and record outcomes.

## CISSP control objectives (thick)
- Security awareness and training alignment with social engineering risks.
- Least privilege and separation of duties for posture toggles.
- Change control with documented approvals and rollback steps.
- Defense in depth and monitoring to detect policy drift.
- Risk management with residual risk acceptance for lab-only tests.
- Auditability through evidence logs and chain of custody.
- Availability and integrity preserved through reversible changes.

## Expected signals/telemetry
- Policy changes logged with clear timestamps.
- Detection alerts fire for posture drift and abuse attempts.
- Revert actions restore baseline signals.

## Steps to run
1) Confirm lab-only scope and warnings.
2) Run apply and capture signals.
3) Run revert and confirm baseline.
4) Store evidence in `docs/logs/` and update `docs/progress.md`.

## Validation checklist
- Each posture has apply/revert automation.
- Alerts and logs validate detection coverage.
- Evidence logs linked in `docs/progress.md`.

## Rollback/Revert
- Use posture revert steps for each test.
- Restore baseline configs and document residual risk.
