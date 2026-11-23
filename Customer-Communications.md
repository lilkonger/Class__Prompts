# Customer Communications: Case CS-2026-1048

> **Training Scenario:** All organizations, people, systems and messages in this file are fictional.
> Created for Microsoft 365 Copilot demonstrations. **Sensitivity: General**

| Field | Details |
|---|---|
| **Customer** | Northstar Financial Services (Fictional) |
| **Case ID** | CS-2026-1048 |
| **Subject** | Cloud Backup Failures |
| **Thread period** | November 19–22, 2026 |

---

## Message 1 — Customer reports the issue

**From:** Priya Raman, IT Operations Director, Northstar Financial Services
**To:** Support Team
**Date:** November 19, 2026, 8:05 AM ET
**Subject:** URGENT: Overnight backup failures on critical systems

Hello Support Team,

Since November 17, several of our scheduled backup jobs have failed, mostly overnight. The affected systems include Financial Reporting, our Customer Records Database and Loan Servicing.

We have not lost any data, but we are worried that we cannot recover these systems if we have an outage. Our internal recovery objective for critical systems is 24 hours.

Please let us know:

1. Why the jobs are failing.
2. Whether our existing backups can be restored.
3. When we can expect a fix.

Regards,
Priya Raman

---

## Message 2 — Support acknowledgement

**From:** Jordan Lee, Support Engineer
**To:** Priya Raman
**CC:** Sam Ortiz, Account Manager
**Date:** November 19, 2026, 9:25 AM ET
**Subject:** RE: URGENT: Overnight backup failures on critical systems

Hi Priya,

Thank you for reporting this. I understand how important reliable backups are for your critical systems.

We have opened case **CS-2026-1048** with **High** priority. Our engineering team is reviewing the job history and diagnostic logs now.

I will send you an update by **5:00 PM ET today**.

Best regards,
Jordan Lee

---

## Message 3 — Infrastructure context from the customer

**From:** Marcus Bell, Infrastructure Manager, Northstar Financial Services
**To:** Jordan Lee
**CC:** Priya Raman
**Date:** November 19, 2026, 2:30 PM ET
**Subject:** RE: URGENT: Overnight backup failures on critical systems

Hi Jordan,

In case it helps: we finished a storage and virtualization update on November 16. Our overnight workload has grown by about 30% since then.

Marcus

---

## Message 4 — Daily status update

**From:** Sam Ortiz, Account Manager
**To:** Priya Raman
**CC:** Jordan Lee; Alex Chen
**Date:** November 20, 2026, 5:00 PM ET
**Subject:** Daily update: Case CS-2026-1048

Hi Priya,

Here is today's update.

- **What we know:** Most failures happen between 1:00 and 3:00 AM ET. We see network timeouts to cloud storage and expired access tokens on long-running jobs.
- **What we are doing:** Our network team is testing the connection from your Toronto data centre. Support has started test restores for your three critical applications.
- **What we don't know yet:** The root cause is not confirmed.

Next update: November 21, 5:00 PM ET.

Sam Ortiz

---

## Message 5 — Customer escalation

**From:** Priya Raman
**To:** Sam Ortiz
**CC:** Jordan Lee; Alex Chen
**Date:** November 21, 2026, 3:40 PM ET
**Subject:** RE: Daily update: Case CS-2026-1048

Sam,

I've learned that the Customer Records Database has had no successful backup since November 17. That is outside our recovery objective.

Before Monday, I need:

- Confirmation that customer records can be recovered.
- A written remediation plan with dates.
- A clear owner on your side.

Our leadership team is asking for a briefing on Tuesday.

Priya

---

## Message 6 — Proposed mitigation

**From:** Alex Chen, Escalation Engineer
**To:** Priya Raman; Marcus Bell
**CC:** Sam Ortiz; Jordan Lee
**Date:** November 22, 2026, 9:30 AM ET
**Subject:** Proposed temporary mitigation for CUSTREC-SQL-01

Hi Priya and Marcus,

The latest verified recovery point for the Customer Records Database is **November 17, 1:10 PM ET**. A test restore of that point succeeded.

To reduce risk while we confirm the root cause, we propose:

1. Moving the full backup for CUSTREC-SQL-01 to 10:00 PM ET, before the busiest network period.
2. Splitting the job into two smaller jobs, so each finishes before its access token expires.

We need your approval to make this change. Can we review it on a call on November 23?

Alex Chen

---

*This document contains synthetic information for training purposes only.*
