# User Lifecycle Management in Microsoft Entra ID

> Hands-on project to learn how to manage the full user lifecycle in Entra ID: **Joiner, Mover, and Leaver**.

This is a hands-on, manual walkthrough in the Microsoft Entra ID portal.

You will create a user, create a group, assign membership, reset a password, disable and re-enable an account, review sign-in logs, simulate a promotion and an offboarding, run an Access Review, and configure a Break Glass account with Conditional Access.

> 📷 **How to view this lab:** click any section below. Each link opens its folder, and inside that folder you will see the full steps with the images already visible inline, no need to click each image link.

---

## Table of Contents

- [What You Will Learn](#what-you-will-learn)
- [Prerequisites](#prerequisites)
- [Repository Structure](#repository-structure)
- [Index - Open a folder to see it](#index---open-a-folder-to-see-it)
- [Best Practices and Security](#best-practices-and-security)
- [Lab Cleanup](#lab-cleanup)
- [Disclaimer](#disclaimer)

---

## What You Will Learn

| Topic | What It Demonstrates |
| --- | --- |
| **User Lifecycle / JML** | Taking a user from onboarding to active status, changing their role, and handling their departure. |
| **Access Control** | Why you should always assign permissions through groups, never directly to users. |
| **Security Protocol** | Why it is critical to disable accounts immediately upon employee exit to prevent unauthorized access. |
| **Monitoring** | How to use Sign-in logs to audit activity and spot security threats. |
| **The Big Picture** | How these manual steps lay the foundation for automated identity governance in enterprise production environments. |

---

---

## Prerequisites

1. Create a free Azure account or a pay-as-you-go account at [Azure: Purchase Options](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account?icid=azurefreeaccount).
2. Have a card ready for registration. Without it, the portal will return errors. Keep at least 1 USD available for verification.
3. A Microsoft Entra ID tenant. In this lab the primary domain is `diegojose0405gmail.onmicrosoft.com`.
4. A Global Administrator or User Administrator role in the tenant to create users and groups.

> ⚠️ **Security:** Never publish real passwords, Tenant IDs, Object IDs, or secrets on GitHub. In this README, temporary passwords appear as `[temporary password]` and must be stored outside the repository.

---

---

## Repository Structure

Each section lives in its own folder with its own README and its own images. When you open a folder on GitHub, the images show directly in the page.

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

> 📷 **How images work here:** in each folder README, images are embedded as `![Description](./images/name.png)`, so they render inline on GitHub. You do not need to click a link to see them.

---

## Index - Open a folder to see it

Click a title to open its folder. Inside you will find the full steps and all the screenshots visible inline.

### [1 · Create a User Manually](01-create-user-manually/)

Create Lucia Fernandez in Entra ID with job info and verify the account is enabled.

![1 · Create a User Manually - preview](01-create-user-manually/images/01-entra-id.png)

[Open folder →](01-create-user-manually/)

### [2 · Create a Group and Assign Membership](02-create-group-and-assign-membership/)

Create the Engineering Team security group and assign Lucia Fernandez to it.

![2 · Create a Group and Assign Membership - preview](02-create-group-and-assign-membership/images/07-groups-overview.png)

[Open folder →](02-create-group-and-assign-membership/)

### [3 · Reset Password, Disable, and Re-enable an Account](03-reset-password-disable-and-re-enable-an-account/)

Reset the password, disable the account for a Leaver, and re-enable it again.

![3 · Reset Password, Disable, and Re-enable an Account - preview](03-reset-password-disable-and-re-enable-an-account/images/11-reset-password-button.png)

[Open folder →](03-reset-password-disable-and-re-enable-an-account/)

### [4 · Sign-in Logs: Audit and Monitoring](04-sign-in-logs-audit-and-monitoring/)

Audit who signed in, from where, and spot failed attempts in Sign-in logs.

![4 · Sign-in Logs: Audit and Monitoring - preview](04-sign-in-logs-audit-and-monitoring/images/15-monitoring-sign-in-logs-menu.png)

[Open folder →](04-sign-in-logs-audit-and-monitoring/)

### [5 · Mover and Leaver: Promotion and Offboarding Simulation](05-mover-and-leaver-promotion-and-offboarding/)

Simulate a promotion from Mid Level to Senior Level and an offboarding to Former Employees.

![5 · Mover and Leaver: Promotion and Offboarding Simulation - preview](05-mover-and-leaver-promotion-and-offboarding/images/17-four-groups.png)

[Open folder →](05-mover-and-leaver-promotion-and-offboarding/)

### [6 · Access Review](06-access-review/)

Create a demo group and app, run an Access Review, and verify the result in My Access.

![6 · Access Review - preview](06-access-review/images/24-access-review-group.png)

[Open folder →](06-access-review/)

### [7 · Break Glass and Conditional Access](07-break-glass-and-conditional-access/)

Create a Break Glass admin and exclude it from a Conditional Access policy.

![7 · Break Glass and Conditional Access - preview](07-break-glass-and-conditional-access/images/29-breakglass-admin.png)

[Open folder →](07-break-glass-and-conditional-access/)


---

## Best Practices and Security

- **Never assign permissions directly to a user.** Always use groups.
- **Never publish passwords, Tenant IDs, Object IDs, or secrets on GitHub.** If you already published a password, change it immediately.
- **Disable the account as soon as the employee leaves.** Do not delete it the same day if you need to audit it, but do disable it.
- **Document every change with screenshots and dates.** That way you can demonstrate the process in an interview or an audit.
- **Use clear and consistent names** for users, groups, and policies: `New Hire Group`, `Mid Level Group`, `Senior Level Group`, `Former Employees`.
- **Review the Sign-in logs** after every important change.

---

## Lab Cleanup

When you finish the practice:

1. Delete the test users.
2. Delete the test groups.
3. Delete the test applications and access reviews.
4. Verify that no account that should be disabled is still enabled.

---

---

## Disclaimer

Organization and writing were assisted by AI, but all steps, explanations, and research were done by Diego Yonoff.

> La organización y redacción fue con ayuda de IA, pero todos los pasos, explicación e investigaciones fueron hechos por Diego Yonoff.
