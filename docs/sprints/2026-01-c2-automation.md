# Sprint Plan: Command and Control (C2) Automation (2026-01)

## Purpose
Automate a lab-only C2 framework to support purple team emulation and detection engineering.

## Preconditions
- Backlog item BL-046 exists in `docs/backlog.md`.
- Lab segmentation and safe egress controls defined.

## Scope
- Setup a C2 framework with user management and RBAC.
- Automate listeners, stagers, agent lifecycle, and tasking workflows.
- Standardize reporting and evidence capture for C2 activity.
- Ensure portability across lab environments.

## Out of scope
- C2 activity outside the lab.
- Unapproved persistence mechanisms.

## Milestones
- M1 C2 framework deployment (Day 1)
- M2 Listener/stager automation (Days 2-3)
- M3 Validation evidence captured (Day 4)

## Work items (Backlog)
- BL-046: Command and control (C2) automation

## Agent assignments
- PM: scope lock, approvals, and comms in `docs/progress.md`.
- Builder: C2 automation and safeguards.
- Analyst: validation and evidence capture.

## Purple team breakdown
- Red: define C2 emulation requirements.
- Blue: tune detections for beaconing and command execution.
- Purple: align evidence with detection gaps.

## CISSP control objectives (thick)
- Least privilege and controlled access to C2 infrastructure.
- Auditability with full command and session logging.
- Change control for listeners and payload configs.
- Risk management and containment of C2 channels.

## Expected signals/telemetry
- Beaconing patterns visible in network telemetry.
- Endpoint alerts for command execution and persistence attempts.
- Evidence logs capturing session history.

## Steps to run
1) Deploy C2 framework in lab.
2) Create listeners, stagers, and agents.
3) Execute lab-only actions and capture evidence.
4) Validate detections and reporting.

## Validation checklist
- C2 framework operational with access controls.
- Alerts generated for beaconing and tasking.
- Evidence logs saved in `docs/logs/`.

## Rollback/Revert
- Decommission listeners and remove agents.
- Restore lab snapshots and revoke credentials.
