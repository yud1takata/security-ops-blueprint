# Sprint Plan: Active Information Gathering Automation (2026-01)

## Purpose
Automate active discovery workflows to validate detection coverage and asset visibility in the lab.

## Preconditions
- Backlog item BL-039 exists in `docs/backlog.md`.
- Lab network segments and scope boundaries defined.

## Scope
- Host discovery and port/service enumeration.
- OS fingerprinting and service banner collection.
- File-sharing and remote-access enumeration with controlled noise levels.
- User enumeration tests under noisy auth controls (lab-only).
- MAC spoofing workflows for lab-only testing.
- Evasion technique validation and framework-based scan workflows.
- Automation in portable playbooks and scripts with rate limits.

## Out of scope
- Unbounded scanning outside lab scope.
- Exploit delivery or destructive tests.

## Milestones
- M1 Target list and rate limits (Day 1)
- M2 Automation and output parsing (Days 2-3)
- M3 Validation evidence captured (Day 4)

## Work items (Backlog)
- BL-039: Active information gathering automation

## Agent assignments
- PM: scope lock, noise thresholds, and approvals.
- Builder: scan automation and parsing.
- Analyst: validation and evidence capture.

## Purple team breakdown
- Red: define discovery objectives and attack surface focus.
- Blue: tune detections for scans and auth probing.
- Purple: align expected telemetry with validation steps.

## CISSP control objectives (thick)
- Availability protection through rate limiting and safe scanning.
- Least privilege and controlled access to scan tooling.
- Auditability via captured logs and scan artifacts.
- Risk management and change control for scan profiles.

## Expected signals/telemetry
- Firewall/IDS alerts for scans and auth probes.
- Service enumeration artifacts stored for review.
- Auth failure logs for user enumeration tests.

## Steps to run
1) Confirm scope and rate limits.
2) Execute active discovery automation.
3) Parse results and store evidence.
4) Review detections and tuning gaps.

## Validation checklist
- Scan outputs are normalized and timestamped.
- Alerts observed for probing activity.
- Evidence logs stored in `docs/logs/`.

## Rollback/Revert
- Disable scan automation and remove artifacts.
- Update scope if noisy controls were exceeded.
