# Lab 02 — Microsoft Entra ID & Conditional Access

**Project Status:** Completed  
**Environment:** Microsoft Entra ID  
**Focus:** Cloud Identity Administration, Multifactor Authentication (MFA), Conditional Access, and Security Policy Validation

---

## 1. Project Overview

This project demonstrates cloud identity administration and access security using Microsoft Entra ID.

I configured departmental identities and security groups, explored authentication security settings, created three Conditional Access policies, and evaluated their behavior using Microsoft's What If simulation tool.

All three Conditional Access policies were configured in **report-only mode**, allowing me to test policy applicability without enforcing access restrictions on live users.

## 2. Business Scenario

A fictional organization wants to strengthen access security across three departments:

- **IT:** Require Microsoft Authenticator MFA.
- **Finance:** Restrict access originating outside the United States.
- **Human Resources:** Restrict access from non-Windows devices.

As the IAM administrator, my responsibilities were to configure the security controls, evaluate their applicability, and document the results before any production enforcement.

## 3. Tools & Technologies

- Microsoft Entra Admin Center
- Microsoft Entra ID
- Microsoft Authenticator
- Conditional Access
- Authentication strengths
- Named locations
- Conditional Access What If tool
- Cloud security groups

## 4. Cloud Identity Administration

I worked with the following test identities:

| User | Department / Purpose |
|---|---|
| Jessica Davis | Human Resources |
| Michael Brown | Information Technology |
| Sarah Johnson | Finance |
| Marcia Lab Admin | Administrative test account |
| Marcia Wagner | Lab identity |

I reviewed the following departmental security groups:

| Security Group | Assigned Test User |
|---|---|
| GG_HR_Users | Jessica Davis |
| GG_IT_Users | Michael Brown |
| GG_Finance_Users | Sarah Johnson |

**Technical Explanation**

Security groups allow organizations to target access controls according to business responsibilities rather than applying identical restrictions to every user.

Using departmental groups also makes access policies easier to maintain when employee responsibilities change.

## 5. Authentication Security Configuration

I reviewed Microsoft Entra authentication methods and configured Microsoft Authenticator settings, including push notification security features and a registration campaign targeting the IT security group.

I also created a custom authentication strength:

`IAM-Lab-Authenticator-MFA`

This authentication strength was configured to allow password plus Microsoft Authenticator push authentication.

**Security Objective:** Establish a defined authentication requirement that could be referenced by a Conditional Access policy.

## 6. Conditional Access Policy 01 — IT MFA Requirement

**Policy Name:** `CA-01-IT-Require-Authenticator-MFA`

**Configuration:**

- Target group: `GG_IT_Users`
- Excluded account: Marcia Lab Admin
- Target resources: All resources
- Grant control: Require authentication strength
- Authentication strength: `IAM-Lab-Authenticator-MFA`
- Policy state: Report-only

**Business Purpose**

Require IT employees to meet a defined MFA requirement when accessing organizational resources.

**Testing and Results**

I used the What If tool to evaluate an IT employee scenario involving Michael Brown.

The simulation showed that the policy applied to the targeted IT identity.

Testing a user outside the IT group showed that the policy did not apply because the user was outside the targeted user/group scope.

**Verified Outcome:** The policy's group targeting and authentication-strength requirement were evaluated successfully through simulation.

## 7. Conditional Access Policy 02 — Finance Geographic Restriction

**Policy Name:** `CA-02-Finance-Block-Non-US-Access`

**Named Location:** `IAM-Lab-United-States`

**Configuration:**

- Target group: `GG_Finance_Users`
- Excluded account: Marcia Lab Admin
- Target resources: All resources
- Network conditions: Include any location; exclude the named United States location
- Grant control: Block access
- Policy state: Report-only

**Business Purpose**

Restrict Finance department access attempts originating outside the organization's permitted geographic area.

**Testing and Results**

I evaluated Finance sign-in scenarios using the Conditional Access What If tool.

| Test Scenario | Simulation Result |
|---|---|
| Finance user accessing from the United States | Finance restriction not applicable because of the location exclusion |
| Finance user accessing from outside the United States | Finance block policy applicable |
| IT user accessing from outside the United States | Finance block policy not applicable because the user was outside the targeted Finance group |

**Verified Outcome:** The What If simulations demonstrated how the geographic condition and departmental group targeting affected policy applicability.

These were simulated outcomes, not actual blocked sign-ins.

## 8. Conditional Access Policy 03 — HR Device Platform Restriction

**Policy Name:** `CA-03-HR-Block-Non-Windows-Devices`

**Configuration:**

- Target group: `GG_HR_Users`
- Excluded account: Marcia Lab Admin
- Target resources: All resources
- Device platforms: Include any device; exclude Windows
- Grant control: Block access
- Policy state: Report-only

**Business Purpose**

Evaluate a restriction designed to prevent HR users from accessing company resources using non-Windows platforms.

**Testing and Results**

| Test Scenario | Simulation Result |
|---|---|
| HR user accessing from Windows | HR restriction not applicable because Windows was excluded |
| HR user accessing from a non-Windows platform | HR block policy applicable |

**Verified Outcome:** Simulation results demonstrated that device platform conditions affected the policy's applicability.

A device-platform condition is not the same as verifying that a device is managed or compliant.

## 9. Conditional Access Validation

I evaluated the policies using the Microsoft Entra What If tool, including positive and negative test conditions involving department membership, geographic location, and device platform.

The test scenarios helped demonstrate:

1. Targeted policies apply to users within their assigned groups.
2. Users outside a targeted group may be excluded from that policy.
3. Geographic conditions affect Finance policy applicability.
4. Device platform conditions affect HR policy applicability.
5. Report-only mode allows administrators to evaluate policy behavior without enforcing it.

**Important:** The What If tool simulates policy applicability. It does not independently demonstrate successful MFA completion, real access denial, or enforcement on an actual sign-in.

## 10. Security Considerations

### Least Privilege and Department-Based Controls

Different departments may require different authentication and access restrictions depending on business responsibilities.

### Administrative Account Exclusion

The lab administrator was excluded from the tested policies to reduce the possibility of administrative lockout during configuration.

### Controlled Policy Rollout

Report-only mode provides an opportunity to evaluate policies before administrators consider enforcement.

### Geographic and Device-Based Restrictions

Location and device platform restrictions can contribute to access security, but they do not replace broader authentication, device compliance, and security monitoring controls.

## 11. Evidence & Screenshots

Original screenshots will be added to document:

- Microsoft Entra identities and security groups
- Authentication methods and the custom MFA authentication strength
- IT Conditional Access policy configuration
- IT positive and negative What If tests
- Finance geographic restriction configuration and simulation
- HR device restriction configuration and simulation
- Final report-only policy inventory

Each screenshot will include a technical explanation and the specific result it supports.

## 12. Skills Demonstrated

- Microsoft Entra ID administration
- Cloud user and group management
- Microsoft Authenticator configuration
- Multifactor authentication concepts
- Custom authentication strengths
- Conditional Access policy configuration
- Named locations
- Group-based policy targeting
- Geographic and device platform conditions
- What If security policy testing
- Report-only policy validation
- Technical documentation

## 13. Lessons Learned

This project strengthened my understanding of how Microsoft Entra ID evaluates access policies using users, groups, authentication requirements, locations, and device conditions.

I learned how to design departmental Conditional Access policies, compare expected and simulated behavior, and document outcomes without confusing simulated security decisions with enforced production restrictions.

The project also reinforced the importance of testing access policies before enforcement to reduce unintended business disruption.

---

**Project Type:** Independent hands-on IAM training lab  
**Portfolio Owner:** Marcia Wagner
