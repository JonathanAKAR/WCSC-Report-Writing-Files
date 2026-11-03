# SOC Ticket Writing Practical

## Ticket Information

**Ticket ID:** SOC-2026-4471
**Alert Rule:** Potential Brute Force Activity
**Alert Severity:** Medium
**Analyst Assigned:** (You)
**Date/Time of Alert:** November 3rd, 2026 at 14:22 UTC

---

## Evidence Log

### Alert Details

- **Source IP:** 203.0.113[.]47
- **Destination IP:** 10.10.5[.]20
- **Destination Hostname:** VPN-GW-01 (Fortinet SSL VPN gateway)
- **Destination Port:** TCP/443
- **Alert Trigger:** 87 failed login attempts in 12 minutes followed by 1 successful authentication

### Authentication Logs

- 87 failed login attempts from 203.0.113[.]47 between 14:10 and 14:22 UTC targeting multiple usernames
- Successful login at 14:22 UTC with username `mwilliams` (Marketing department)
- MFA is not enabled on the VPN gateway
- `mwilliams` account had no VPN login history in the prior 90 days

### Threat Intelligence

- 203.0.113[.]47 flagged on AbuseIPDB with a confidence score of 78% — reports cite brute force and credential stuffing
- IP geolocates to a hosting provider in Romania
- `mwilliams` credentials appeared in a third-party breach dataset (LeakedSource) dated September 2026

### Post-Authentication Activity

- VPN session for `mwilliams` lasted 8 minutes (14:22–14:30 UTC)
- During the session, 3 SMB connections were initiated to internal file server FS-01 (10.10.5[.]50)
- No data transfer volume recorded exceeded baseline thresholds

---

## Instructions

Using the evidence above, write the **Conclusion** and **Recommendations** sections of a SOC ticket report. Your conclusion should clearly state what happened based on the evidence without overstating what can be confirmed. Your recommendations should be specific, actionable, and prioritized.
