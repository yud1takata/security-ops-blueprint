# Sprint Plan: Advanced Directory Attacks + Detection Engineering (2026-01)

## Purpose
Automate advanced directory attack simulations and build detections for high-impact techniques.

## Preconditions
- Backlog item BL-045 exists in `docs/backlog.md`.
- Directory services lab baseline and detection pipeline operational.

## Scope
- Advanced lateral movement and credential abuse simulations (lab-only).
- Ticket abuse simulations and detection tuning.
- Evidence capture for all tests.

## Out of scope
- Any activity outside lab scope.
- Persistence beyond lab-only tests.

## Milestones
- M1 Advanced attack design and safeguards (Day 1)
- M2 Automation and detection updates (Days 2-3)
- M3 Validation evidence captured (Day 4)

## Work items (Backlog)
- BL-045: Advanced directory attacks + detection engineering

## Agent assignments
- PM: scope lock and risk approvals.
- Builder: automation and detection updates.
- Analyst: validation and evidence capture.

## Purple team breakdown
- Red: define advanced attack paths and objectives.
- Blue: implement detections for ticket abuse and lateral movement.
- Purple: validate results and tune detection rules.

## CISSP control objectives (thick)
- Least privilege and separation of duties for privileged tools.
- Auditability and chain of custody for high-impact tests.
- Change control and rollback for directory state.
- Risk management with explicit lab-only scope.

## Expected signals/telemetry
- Authentication anomalies and ticket misuse alerts.
- Lateral movement telemetry for privileged operations.
- Evidence logs documenting attack chains.

## Steps to run
1) Approve advanced attack scope and safeguards.
2) Execute lab-only simulations.
3) Capture telemetry and evidence.
4) Validate detections and update rules.

## Validation checklist
- Detection rules updated and validated.
- Evidence logs saved in `docs/logs/`.
- Lab state restored after tests.

## Rollback/Revert
- Revert lab snapshots and remove test artifacts.
- Reset any modified directory settings.
