# Endpoint Firewall + Middlebox Plan (UFW + Scrubbing + Proxies)

## Purpose
Reduce protocol sprawl and tighten network visibility by enforcing endpoint
firewalls on Linux systems and standardizing traffic control across access
control, traffic scrubbing, and proxies.

## Scope
- Linux endpoints in the environment (SOC, infra, personal services, lab router).
- Edge firewall remains the primary perimeter enforcement point.
- Windows endpoints use native Windows Firewall (tracked separately).

## Preconditions
- Host inventory is current.
- Service ports are tracked in `data/firewall/endpoint-ufw-inventory.yml`.
- Edge firewall policies are up to date.

## Three-Pronged Control Model
### 1) Access Control (UFW)
Goal: enforce policy so analysts only have to reason about a small set of
protocols/ports per endpoint.

Baseline rules:
- Default deny inbound, default allow outbound.
- Allow established/related traffic.
- Allow loopback.
- Allow SSH from the control host only.
- Allow only documented service ports per host.
- Reduce traffic variety to improve NSM detection rates.

Authoritative inventory:
- `data/firewall/endpoint-ufw-inventory.yml`

Analyst workflow:
- If a protocol or port appears that is not in the inventory, treat it as a
  policy violation (access control failure) and investigate.

### 2) Traffic Scrubbing (Normalization)
Goal: reduce ambiguity in packet streams so sensors can interpret traffic
reliably.

Planned scrub points:
- **Edge firewall**: drop invalid TCP flag combinations and normalize fragments.
- **Lab router**: normalize inter-lab traffic to keep sensor data consistent.
- **Sensors**: enable stream reassembly and fragment policies where deployed.

Guidance:
- Favor drop/normalize of malformed fragments and invalid flag combinations.
- Prefer full-content reassembly or drop fragments that cannot be normalized.
- Ensure scrub rules do not break desired features (see RFC 3234).
- Scrubbing is an enforcement layer: traffic that violates norms is dropped
  even if the port is otherwise allowed.

### 3) Proxies (Protocol-Aware Controls)
Goal: enforce application-level access control for allowed protocols.

Current:
- Reverse proxies terminate TLS for SOC and AI services.

Planned:
- Introduce explicit HTTP/HTTPS forward proxies for controlled egress.
- Block direct outbound HTTP(S) except through proxies.
- Evaluate application recognition (NBAR/app-ID) where supported.
- Proxies enforce protocol compliance; non-conforming traffic is denied.

## Endpoint Firewall Inventory
The inventory is the source of truth for UFW rules and analyst expectations:
- `data/firewall/endpoint-ufw-inventory.yml`

## Steps to Run
1) Update `data/firewall/endpoint-ufw-inventory.yml` for the target endpoint.
2) Apply the UFW baseline (planned playbook) to the host group.
3) Validate with the checklist below and capture a log in `docs/logs/`.

## Update Policy (Ports, Services, IPs, New Endpoints)
1) Update the inventory file:
   - Add/remove the service entry in `data/firewall/endpoint-ufw-inventory.yml`.
   - Note the source scope (management subnet, lab subnets, edge firewall only).
2) Update access control:
   - Apply UFW rules (future `ansible/playbooks/blueprint_endpoint_firewall.yml`).
   - Remove deprecated rules when services are retired.
3) Update dependent controls:
   - Reverse proxy configs when service ports move.
   - Validation targets when URLs change.
4) Validate:
   - `ufw status verbose` on each endpoint.
   - `ss -lntup` to confirm only approved listeners.
5) Record:
   - `docs/progress.md` entry + validation log in `docs/logs/`.

Port conflict handling:
- Prefer shifting services to non-conflicting ports on the host.
- Update reverse proxies to keep external ports stable when possible.
- If a conflict is unavoidable, update the inventory and document the change
  with a rollback plan.

## Adversary Emulations (Egress Circumvention)
Use these lab-only scenarios to validate outbound access controls:
- **dhphonehome**: simulate covert outbound callbacks and DNS tunnel attempts.
- **grayworld**: emulate slow, low-and-slow outbound misuse to bypass proxies.

Expected outcome:
- Proxy-only egress blocks direct outbound sessions.
- Non-standard protocols are denied and logged.

## Validation Checklist
- UFW enabled and active on all Linux endpoints.
- UFW rules match the inventory.
- Non-approved ports are closed from the management subnet.
- Monitoring targets remain `UP`.
- SIEM logs show drops for blocked protocols.

## Rollback / Revert
- Revert the inventory commit and reapply the last known-good ruleset.
- Emergency: `ufw disable` on the affected endpoint (lab-only), then restore
  the previous ruleset and re-enable.

## References and Tools
- RFC 3234: Middleboxes: On the Facts of Life.
- Offensive tools (must-know): netcat, hping, nemesis, ettercap, kismet,
  bsd-airtools, xprobe, nmap, amap, nbtscan, nikto, nessus.
- Defensive tools: tcpdump, windump, ethereal (Wireshark), argus, snort.
