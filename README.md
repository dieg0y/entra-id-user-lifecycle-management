# Microsoft Entra ID User Lifecycle Management Lab

![Microsoft Entra ID](https://img.shields.io/badge/Microsoft-Entra_ID-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Identity Management](https://img.shields.io/badge/Identity-Management-success?style=for-the-badge)
![JML](https://img.shields.io/badge/Joiner-Mover-Leaver-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

## Project Overview

This project demonstrates the complete **Joiner-Mover-Leaver (JML)** user lifecycle in **Microsoft Entra ID**, following identity and access management practices commonly used in enterprise environments.

The lab walks through the creation and management of users, group-based access control, auditing, identity governance, Conditional Access, and Break Glass administration.

All tasks were completed manually using the Microsoft Entra Admin Center to provide hands-on experience with real administrative workflows.

---

## Skills Demonstrated

- User Provisioning
- User Lifecycle Management (JML)
- Group-Based Access Control (RBAC Principles)
- Password Administration
- Sign-in Log Analysis
- Security Monitoring
- Access Reviews
- Identity Governance
- Conditional Access
- Break Glass Account Management
- Microsoft Entra Administration
- Security Best Practices

---

## Table of Contents

- [What You Will Learn](#what-you-will-learn)
- [Technologies Used](#technologies-used)
- [Prerequisites](#prerequisites)
- [Repository Structure](#repository-structure)
- [Lab Modules](#lab-modules)
- [Best Practices and Security](#best-practices-and-security)
- [Lab Cleanup](#lab-cleanup)
- [Disclaimer](#disclaimer)

---

## What You Will Learn

| Topic | Description |
|---------|-------------|
| **Joiner Process** | Create and onboard new users. |
| **Group Management** | Assign access through security groups. |
| **Password Management** | Reset user passwords securely. |
| **Mover Process** | Simulate role changes and access modifications. |
| **Leaver Process** | Disable and offboard departing users. |
| **Identity Governance** | Perform Access Reviews. |
| **Security Operations** | Monitor activity through Sign-in Logs. |
| **Conditional Access** | Understand policy-based access control. |
| **Break Glass Accounts** | Configure emergency administrative access. |

---

## Technologies Used

- Microsoft Entra ID
- Microsoft Azure
- Microsoft Identity Governance
- Microsoft Entra Groups
- Conditional Access
- Access Reviews
- Sign-in Logs
- GitHub
- Identity and Access Management (IAM)

---

## Prerequisites

1. Create a Microsoft Azure account:
   - https://azure.microsoft.com/free/

2. Create or use an existing Microsoft Entra ID tenant.

3. Assign one of the following administrative roles:
   - Global Administrator
   - User Administrator

4. Access to the Microsoft Entra Admin Center:
   - https://entra.microsoft.com

> **Security Note:** Never publish real passwords, Tenant IDs, Object IDs, secrets, access tokens, or sensitive information in public repositories.

---

## Repository Structure

```text
/
├── README.md
├── 01-create-user-manually/
│   ├── README.md
│   └── images/
├── 02-create-group-and-assign-membership/
│   ├── README.md
│   └── images/
├── 03-reset-password-disable-and-re-enable-an-account/
│   ├── README.md
│   └── images/
├── 04-sign-in-logs-audit-and-monitoring/
│   ├── README.md
│   └── images/
├── 05-mover-and-leaver-promotion-and-offboarding/
│   ├── README.md
│   └── images/
├── 06-access-review/
│   ├── README.md
│   └── images/
└── 07-break-glass-and-conditional-access/
    ├── README.md
    └── images/
```

Each module contains its own documentation and screenshots.

All screenshots are embedded directly into each module's README file for easier review.

---

## Lab Modules

### 1. Create a User Manually

Simulates the onboarding process for a new employee.

**Covered Topics**

- User creation
- User properties
- Temporary passwords
- Account verification

---

### 2. Create a Group and Assign Membership

Demonstrates access management through security groups.

**Covered Topics**

- Security groups
- Membership assignment
- Access control concepts

---

### 3. Reset Password, Disable, and Re-enable an Account

Demonstrates common Help Desk and Identity Administrator tasks.

**Covered Topics**

- Password reset
- Account disabling
- Account reactivation

---

### 4. Sign-in Logs: Audit and Monitoring

Introduces security auditing within Entra ID.

**Covered Topics**

- Sign-in logs
- Audit trail analysis
- Security monitoring

---

### 5. Mover and Leaver: Promotion and Offboarding

Simulates employee role changes and departures.

**Covered Topics**

- Promotions
- Group reassignment
- Access removal
- Account offboarding

---

### 6. Access Review

Introduces identity governance concepts.

**Covered Topics**

- Access Reviews
- Access validation
- Governance workflows

---

### 7. Break Glass and Conditional Access

Covers emergency access administration and policy enforcement.

**Covered Topics**

- Break Glass accounts
- Conditional Access
- Administrative resilience

---

## Best Practices and Security

- Use groups instead of assigning permissions directly to users.
- Follow the principle of least privilege.
- Remove access that is no longer required.
- Disable accounts immediately when employees leave the organization.
- Review sign-in logs regularly.
- Store credentials securely.
- Maintain administrative emergency access accounts.
- Document administrative actions with screenshots when building a lab portfolio.

---

## Lab Cleanup

After completing the lab:

1. Delete all test users.
2. Delete all test groups.
3. Remove test policies if they are no longer needed.
4. Complete or remove Access Reviews.
5. Verify that disabled accounts remain disabled.
6. Review the tenant to ensure no unnecessary objects remain.

---

## Learning Outcome

After completing this lab, you will understand how organizations manage user identities throughout the entire employment lifecycle while maintaining security, compliance, and governance requirements.

This project provides foundational experience for roles such as:

- Help Desk Technician
- IT Support Specialist
- Microsoft 365 Administrator
- Identity Administrator
- IAM Analyst
- Systems Administrator

---

## Disclaimer

This project was created, tested, and validated by **Diego Yonoff**.

Artificial Intelligence tools were used solely to assist with documentation formatting, grammar improvements, and content organization.

All configurations, testing, screenshots, validation, and administrative actions were performed manually within a Microsoft Entra ID environment.

The project is intended for educational and portfolio purposes only.
