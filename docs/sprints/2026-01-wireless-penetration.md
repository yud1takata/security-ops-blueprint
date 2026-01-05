# Sprint Plan: Wireless Penetration Testing Automation (2026-01)

## Purpose
Automate baseline wireless penetration testing workflows for lab assurance and detection engineering.

## Preconditions
- Backlog item BL-047 exists in `docs/backlog.md`.
- Wireless lab hardware and adapters validated.

## Scope
- Enterprise wireless authentication flows and RADIUS setup.
- SDR-based lab tooling and adapter configuration.
- Monitor mode enablement and capture workflows.
- Automation with portable configs and safety controls.

## Out of scope
- Wireless attacks outside lab scope.
- Live production testing.

## Milestones
- M1 Wireless lab readiness (Day 1)
- M2 Automation and capture workflows (Days 2-3)
- M3 Validation evidence captured (Day 4)

## Work items (Backlog)
- BL-047: Wireless penetration testing automation

## Agent assignments
- PM: scope lock and approvals.
- Builder: wireless automation and tooling.
- Analyst: validation and evidence capture.

## Purple team breakdown
- Red: define wireless attack scenarios.
- Blue: tune detections for wireless events.
- Purple: align evidence with detection gaps.

## CISSP control objectives (thick)
- Availability and safety controls for RF testing.
- Least privilege for wireless tooling access.
- Auditability of captures and authentication events.
- Risk management with strict scope boundaries.

## Expected signals/telemetry
- RADIUS auth logs and wireless association events.
- IDS alerts for deauth and scanning behaviors.
- Evidence logs for capture workflows.

## Steps to run
1) Provision wireless lab and RADIUS.
2) Configure adapters and capture tooling.
3) Execute lab-only tests and capture evidence.
4) Validate detections and update runbooks.

## Validation checklist
- Wireless tooling automation works on fresh lab setup.
- RADIUS events visible in logs.
- Evidence logs saved in `docs/logs/`.

## Rollback/Revert
- Disable wireless test SSIDs and revert configs.
- Remove capture files and reset adapters.
