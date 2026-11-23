
# Lab 03 — Identity Governance & Access Reviews

**Project Status:** Completed  
**Environment:** Microsoft Entra ID — Personal Training Tenant  
**Focus:** Access Recertification, Identity Governance, Least Privilege, and Access Remediation  
**Completion Date:** November 10, 2026

---

## 1. Project Overview

This project demonstrates how identity governance processes can help organizations review employee access, identify unnecessary permissions, and remove access that is no longer justified by business responsibilities.

I configured and completed a Microsoft Entra ID access review for a Finance security group. Using a simulated employee department-transfer scenario, I evaluated the employee's continued need for access, recorded a denial decision, applied the review results, and independently verified that the employee was removed from the Finance group.

Unlike a theoretical access review, this exercise included an actual membership removal in my training environment.

## 2. Business Scenario

A fictional organization conducts periodic access recertification to ensure employees retain only the access required for their assigned responsibilities.

Sarah Johnson, a Finance group member, was used in a simulated scenario in which she transferred from Finance to Human Resources.

Following the simulated transfer, Sarah no longer had a business need for Finance group access.

**Security concern:** Retaining unnecessary Finance access could expose sensitive business resources and conflict with least-privilege principles.

**Objective:** Conduct an access recertification review, document the decision, remove unnecessary group membership, and verify the outcome.

The department transfer was a business scenario, not a change made to Sarah's actual department or HR group membership.

## 3. Tools and Technologies

- Microsoft Entra ID
- Microsoft Entra Identity Governance
- Access Reviews
- Microsoft Entra Security Groups
- My Access review interface
- Access review decision and result-management features

## 4. Identity and Group Scope

**Access review name:** `AR-01-Finance-Access-Recertification`

**Target group:** `GG_Finance_Users`

**Reviewed identity:** Sarah Johnson

**Reviewer:** Marcia Lab Admin

**Review type:** Group membership access review

**Review frequency:** One-time

The review targeted the Finance group's membership rather than all users or all applications in the tenant.

## 5. Access Review Configuration

I created the Finance access recertification review with the following settings:

| Setting | Configuration |
|---|---|
| Review name | `AR-01-Finance-Access-Recertification` |
| Resource | `GG_Finance_Users` |
| Review scope | All users in the selected group |
| Reviewer | Marcia Lab Admin |
| Frequency | One time |
| Review period | November 10–11, 2026 |
| Duration | 1 day |
| Auto-apply results | Disabled |
| No-response action | No change |
| Decision helper | No sign-in within 30 days |
| Require justification | Enabled |
| Email notifications | Enabled |
| Email reminders | Enabled |

**Security rationale:** Disabling automatic application allowed the review decision and subsequent remediation to be handled deliberately.

Requiring a justification supported accountability by recording the reason for the decision.

## 6. Review Execution

After creating the access review, I accessed the assigned review through the My Access interface.

The review displayed Sarah Johnson as the identity requiring recertification.

The recommendation shown in the interface was **Deny**, based on the configured inactivity-related decision helper.

I evaluated the recommendation against the simulated business scenario and made a manual decision to deny continued Finance membership.

**Decision:** Deny

**Business justification:** Sarah Johnson was treated as having transferred from Finance to Human Resources and therefore no longer required Finance group access.

This decision was made manually rather than relying solely on the automated recommendation.

## 7. Review Completion

After submitting the decision, the review showed that its single user had been reviewed.

The review was then stopped and marked complete.

Because the review was configured with automatic application disabled, completing the review did not by itself remove the membership.

The application of results was handled as a separate administrative action.

## 8. Applying Access Review Results

I manually applied the completed access review results in Microsoft Entra ID.

The results interface reported:

**Status:** Success

**Action:** Successfully removed from membership

**Applied by:** Marcia Lab Admin

**Date:** November 10, 2026

This established that the denied access decision had been applied to the Finance group membership in the training environment.

## 9. Independent Membership Verification

To verify the remediation independently of the review results page, I navigated to the Finance security group in Microsoft Entra ID.

**Group:** `GG_Finance_Users`

**Location:** Members → Direct members

The membership view displayed:

`0 group members found`

`No members have been found`

This confirmed that Sarah Johnson's direct membership in the Finance group had been removed.

The verification establishes the group membership outcome, not the status of every possible permission or resource assignment elsewhere in the tenant.

## 10. Security Analysis and Business Relevance

### Access Recertification

Access reviews support periodic reassessment of whether users still require the access they hold.

### Least Privilege

The scenario demonstrates removing group membership when it is no longer justified by an employee's assigned responsibilities.

### Separation of Decision and Remediation

A review decision and the application of that decision are distinct steps when automatic application is disabled.

### Auditability

Documenting the reviewer, denial justification, review status, application result, and follow-up verification provides a traceable record of administrative actions.

### Verification

Checking the group's membership after applying results provides stronger evidence of remediation than relying solely on the recorded decision.

## 11. Evidence & Screenshots

Original screenshots from the completed Lab 3 exercise will be uploaded to this folder and embedded here with individual technical explanations.

The evidence will document:

- Access review configuration and scope
- Review scheduling and reviewer settings
- My Access review assignment
- The recommended decision and manual denial
- The documented business justification
- Completion of the access review
- Manual application of review results
- Successful membership removal
- Independent verification of the Finance group's direct membership

Each evidence image will include its configuration, technical explanation, business relevance, and verified outcome.

## 12. Skills Demonstrated

- Microsoft Entra Identity Governance
- Access review creation and configuration
- Access recertification
- Security group membership review
- Manual access decision-making
- Least-privilege analysis
- Review justification documentation
- Manual application of review results
- Group membership remediation
- Independent verification of access removal
- Security documentation and audit evidence

## 13. Lessons Learned

This project reinforced that access governance involves more than identifying potentially excessive permissions.

An effective review workflow includes evaluating business need, documenting an access decision, applying the decision, and verifying the actual change.

I also learned why a completed access review does not necessarily mean access has already been removed, especially when automatic application is disabled.

The independent membership verification demonstrated the value of confirming the result directly in the affected resource.

---

**Environment note:** This project was completed in a personal Microsoft Entra ID training environment using simulated employee identities and a fictional business scenario. The access review and group membership removal were performed in the lab tenant, not a production organization.
