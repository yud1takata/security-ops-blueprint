# Sprint Plan: Status Endpoint + Health Rollout (2026-01)

## Purpose
Deliver a standardized /status endpoint and a unified service health view to improve availability monitoring and operational assurance.

## Preconditions
- Backlog item BL-035 exists in `docs/backlog.md`.
- Service owners identified for core platforms.
- Validation playlist exists in `docs/validation-playlist.md`.

## Scope
- Define /status schema (service, dependencies, version, health, and timestamps).
- Add /status endpoints to core services where missing.
- Deploy a status view/dashboard with auth, rate limiting, and logging.
- Automate health checks and alerting with portable, variable-driven configuration.
- Capture validation evidence in `docs/logs/`.

## Out of scope
- Public internet exposure without explicit approval.
- Vendor-specific dashboards tied to single environments.

## Milestones
- M1 /status schema approved (Day 1)
- M2 Endpoints implemented and automated (Days 2-3)
- M3 Status view + alerting wired (Day 4)
- M4 Validation evidence captured (Day 5)

## Work items (Backlog)
- BL-035: Status endpoint + health rollout

## Agent assignments
- PM: scope lock, owner coordination, and comms in `docs/progress.md`.
- Builder: endpoint scaffolds, automation, and dashboards.
- Analyst: validation, evidence capture, and alert checks.

## Purple team breakdown
- Red: simulate service degradation to validate detection.
- Blue: tune alerting and response playbooks.
- Purple: document lessons learned and update validation steps.

## CISSP control objectives (thick)
- CIA triad alignment: confidentiality, integrity, availability for health data.
- Least privilege and need-to-know for status access.
- Separation of duties for endpoint changes and monitoring.
- Defense in depth via layered checks and alerting.
- Change control with rollback and approvals.
- Auditability: logs, evidence preservation, and traceability.
- Risk management: residual risk documented for blind spots.
- Availability and resilience through redundancy and graceful degradation.

## Expected signals/telemetry
- /status responses show consistent health fields and codes.
- Alerts trigger on health failures and dependency degradation.
- Logs record check frequency and failed checks for audit review.

## Steps to run
1) Approve schema and owners.
2) Implement endpoints and wire checks.
3) Deploy status view and alerting.
4) Validate and store evidence in `docs/logs/`.

## Validation checklist
- /status endpoint returns expected schema for each service.
- Status view shows accurate service states.
- Alert tests recorded with timestamps in evidence logs.

## Rollback/Revert
- Remove /status endpoint changes and revert dashboard configs.
- Update risk register if coverage is reduced.
