# Sprint Plan: Wireless Security Hardening (2026-01)

## Purpose
Automate wireless hardening controls and validate defensive posture in the lab.

## Preconditions
- Backlog item BL-049 exists in `docs/backlog.md`.
- Wireless baseline configuration documented.

## Scope
- SSID management, MAC filtering, and strong authentication policies.
- Power level tuning and antenna placement guidance.
- Enterprise wireless security baselines (EAP/TLS).
- Segmentation and guest isolation controls.
- Validation automation with portable configs.

## Out of scope
- Changes that reduce security without explicit lab-only posture controls.

## Milestones
- M1 Hardening baseline defined (Day 1)
- M2 Automation and validation (Days 2-3)
- M3 Evidence captured (Day 4)

## Work items (Backlog)
- BL-049: Wireless security hardening automation

## Agent assignments
- PM: scope lock and approvals.
- Builder: hardening automation and documentation.
- Analyst: validation and evidence capture.

## Purple team breakdown
- Red: validate controls against lab attack cases.
- Blue: confirm monitoring for wireless anomalies.
- Purple: align controls with detection outcomes.

## CISSP control objectives (thick)
- Availability and integrity for wireless services.
- Least privilege and access control enforcement.
- Defense in depth with segmentation and monitoring.
- Change control with documented rollback guidance.

## Expected signals/telemetry
- Auth success/failure logs reflect policy enforcement.
- Wireless monitoring reflects reduced attack surface.
- Evidence logs capture control validation.

## Steps to run
1) Define hardening baseline and approvals.
2) Apply automation and validate results.
3) Capture evidence and update runbooks.

## Validation checklist
- Hardening controls applied and verified.
- Monitoring and alerting validated.
- Evidence logs saved in `docs/logs/`.

## Rollback/Revert
- Revert wireless configs to baseline.
- Document residual risk for any removed controls.
