# Incident Report: Backup Miss from Resolver Interruption (2026-01-05)

## Purpose
Document a missed backup caused by a transient name resolution failure and track the remediation steps taken.

## Summary
On 2026-01-05, a scheduled hypervisor backup job failed to reach the backup appliance because the resolver was restarting. The immediate mitigation was to shift the backup schedule to a different low-traffic window and document follow-up actions to reduce DNS dependency.

## Impact
- One scheduled backup snapshot missing for the day.
- Recovery point objective temporarily widened until the next successful run.

## Detection
- Hypervisor backup task reported a name resolution error for the backup target.
- Backup appliance showed no new snapshot for the missed run.

## Root cause
- DNS resolver restart overlapped with the scheduled backup job.
- Backup path relied on a single resolver without a fallback.

## Timeline
- 2026-01-05: Scheduled backup job failed due to name resolution error.
- 2026-01-05: Backup schedule moved to a different low-traffic window.

## Remediation
- Shifted the backup schedule to avoid the resolver restart window.
- Documented the failure mode and follow-up actions.

## Lessons learned
- Backup reliability depends on resolver stability and redundancy.
- Scheduling should avoid maintenance activity that impacts name resolution.

## Preventive actions
- Stabilize resolver restarts or move them outside backup windows.
- Add a secondary resolver or a static host entry for the backup target.
- Alert on backup job failures before business hours.
- Add a preflight check that verifies resolver availability.

## Preconditions
- Access to the hypervisor backup job status.
- Access to the backup appliance snapshot view.
- Access to resolver logs for the incident window.

## Steps to run
1) Confirm the backup job is enabled and scheduled.
2) Review the most recent backup task result.
3) Verify that the backup appliance has a current snapshot.
4) Check resolver logs for restarts during the backup window.

## Validation checklist
- Backup job shows enabled status with the updated schedule.
- Latest backup task completes without errors.
- Backup appliance reflects a new snapshot after the next run.

## Rollback/Revert
- Revert the schedule change in the automation and re-apply the backup job configuration.
