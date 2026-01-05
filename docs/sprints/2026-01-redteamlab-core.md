# Sprint Plan: Red Team Lab Core Buildout (2026-01)

## Purpose
Provision a portable, automated red team lab baseline to support purple team detection engineering.

## Preconditions
- Backlog item BL-037 exists in `docs/backlog.md`.
- Base VM templates and network segments are available.

## Scope
- Deploy directory services controller, managed endpoints, and core lab services.
- Create users, admin accounts, and security groups.
- Join endpoints and validate authentication flows.
- Configure file sharing and service accounts to support auth testing.
- Add lab-only posture toggles with explicit revert steps.
- Automate via portable, variable-driven tooling.

## Out of scope
- Production directory services.
- Irreversible weakening of security controls.

## Milestones
- M1 VM provisioning baseline (Day 1)
- M2 Directory services operational (Day 2)
- M3 Users/groups + endpoint joins (Days 3-4)
- M4 Lab-only posture toggles + validation (Day 5)

## Work items (Backlog)
- BL-037: Red team lab core buildout (directory services + endpoints)

## Agent assignments
- PM: scope lock, owner approvals, and comms in `docs/progress.md`.
- Builder: automation for provisioning, directory services, and joins.
- Analyst: validation and evidence capture.

## Purple team breakdown
- Red: define attack surface requirements and success criteria.
- Blue: map detections for directory and file-sharing activity.
- Purple: align automation and validation flow.

## CISSP control objectives (thick)
- IAM alignment with least privilege and separation of duties.
- Accountability and auditability for directory changes.
- Configuration management and baseline control for lab images.
- Defense in depth with monitoring on authentication and group changes.
- Change control and rollback guidance for posture toggles.
- Risk management with lab-only scope and residual risk acceptance.

## Expected signals/telemetry
- Directory changes and join events logged.
- File-sharing auth telemetry visible in SOC pipeline.
- Posture toggles generate expected alerts and revert cleanly.

## Steps to run
1) Provision VMs and validate network placement.
2) Initialize directory services and seed directory objects.
3) Join endpoints and validate login flows.
4) Enable lab-only posture toggles and capture evidence.

## Validation checklist
- Directory services operational with users/groups created.
- Endpoints joined and authenticated.
- Telemetry visible for auth and file sharing.
- Evidence logs saved in `docs/logs/`.

## Rollback/Revert
- Revert posture toggles to baseline.
- Decommission lab VMs if validation fails.
