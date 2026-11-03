# Report Writing Practical

## Scenario

**Client:** Butter Family Farms
**Assessment Type:** External Penetration Test
**Duration:** 5 business days

---

## Findings

| # | Finding | Severity |
|---|---------|----------|
| 1 | Exposed Jenkins server with default credentials | High |
| 2 | Jenkins service account running with Domain Admin privileges | High |
| 3 | Unencrypted database connection strings stored in Jenkins build scripts | High |
| 4 | Customer database accessible from the DMZ with no network segmentation | High |
| 5 | Multi-factor authentication not enforced on VPN gateway | Medium |
| 6 | Expired SSL/TLS certificates on external-facing web servers | Low |
| 7 | Verbose error messages on customer portal exposing internal paths and software versions | Informational |

---

## Attack Chain

1. **Initial Access** — Discovered Jenkins server exposed to the internet. Logged in with default credentials (Finding 1).
2. **Privilege Escalation** — Jenkins service account was configured with Domain Admin privileges, granting full Active Directory access (Finding 2).
3. **Credential Harvesting** — Build scripts on Jenkins contained hardcoded database connection strings in plaintext, including SA credentials for the production database (Finding 3).
4. **Data Access** — Used harvested credentials to connect directly to the customer database from the DMZ due to lack of network segmentation (Finding 4).

**Findings 5–7** are standalone and did not contribute to the attack chain.

---

## Instructions

Research Butter Family Farms to understand the business context — what they do, who their customers are, and what kind of data they'd realistically hold. Use that context to write an executive summary for this penetration test. Don't invent specific numbers; frame the impact in terms of what matters to *this* business.
