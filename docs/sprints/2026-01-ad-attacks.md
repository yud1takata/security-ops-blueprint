# Sprint Plan: Directory Services Attack Automation (2026-01)

## Purpose
Automate baseline directory services attack workflows for purple team detection engineering.

## Preconditions
- Backlog item BL-044 exists in `docs/backlog.md`.
- Directory services lab baseline is complete.

## Scope
- Directory enumeration automation and trust mapping.
- Name resolution abuse simulations (lab-only).
- File-sharing and authentication trust exploitation tests.
- Evidence capture for auth and directory telemetry.

## Out of scope
- Production directory services.
- Irreversible changes to domain state.

## Milestones
- M1 Enumeration workflows defined (Day 1)
- M2 Trust abuse simulations automated (Days 2-3)
- M3 Validation evidence captured (Day 4)

## Work items (Backlog)
- BL-044: Directory services attack automation

## Agent assignments
- PM: scope lock and risk approvals.
- Builder: automation for enumeration and trust abuse.
- Analyst: validation and evidence capture.

## Purple team breakdown
- Red: define objectives and attack paths.
- Blue: tune detections for directory abuse.
- Purple: align evidence with detection requirements.

## CISSP control objectives (thick)
- IAM alignment and least privilege.
- Auditability for directory changes and auth attempts.
- Separation of duties for privileged operations.
- Risk management and containment of attack workflows.

## Expected signals/telemetry
- Directory enumeration artifacts and query spikes.
- Auth anomalies from trust abuse simulations.
- Evidence logs for each workflow.

## Steps to run
1) Confirm lab scope and safety controls.
2) Run enumeration automation and collect evidence.
3) Execute trust abuse simulations.
4) Validate detections and document gaps.

## Validation checklist
- Enumeration outputs stored and timestamped.
- Alerts observed for trust abuse tests.
- Evidence logs saved in `docs/logs/`.

## Rollback/Revert
- Remove test artifacts and revert snapshots.
- Reset affected credentials and policies.
