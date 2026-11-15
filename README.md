# User Lifecycle Management in Microsoft Entra ID

> Hands-on project to learn how to manage the full user lifecycle in Entra ID: **Joiner, Mover, and Leaver**.

This is a hands-on, manual walkthrough in the Microsoft Entra ID portal.

You will create a user, create a group, assign membership, reset a password, disable and re-enable an account, review sign-in logs, simulate a promotion and an offboarding, run an Access Review, and configure a Break Glass account with Conditional Access.

---

## Table of Contents

- [What You Will Learn](#what-you-will-learn)
- [Prerequisites](#prerequisites)
- [Repository Structure](#repository-structure)
- [1 · Create a User Manually](#1--create-a-user-manually)
- [2 · Create a Group and Assign Membership](#2--create-a-group-and-assign-membership)
- [3 · Reset Password, Disable, and Re-enable an Account](#3--reset-password-disable-and-re-enable-an-account)
- [4 · Sign-in Logs: Audit and Monitoring](#4--sign-in-logs-audit-and-monitoring)
- [5 · Mover and Leaver: Promotion and Offboarding Simulation](#5--mover-and-leaver-promotion-and-offboarding-simulation)
- [6 · Access Review](#6--access-review)
- [7 · Break Glass and Conditional Access](#7--break-glass-and-conditional-access)
- [Best Practices and Security](#best-practices-and-security)
- [Lab Cleanup](#lab-cleanup)
- [Pending Screenshots](#pending-screenshots)

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

## Prerequisites

1. Create a free Azure account or a pay-as-you-go account at [Azure: Purchase Options](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account?icid=azurefreeaccount).
2. Have a card ready for registration. Without it, the portal will return errors. Keep at least 1 USD available for verification.
3. A Microsoft Entra ID tenant. In this lab the primary domain is `diegojose0405gmail.onmicrosoft.com`.
4. A Global Administrator or User Administrator role in the tenant to create users and groups.

> ⚠️ **Security:** Never publish real passwords, Tenant IDs, Object IDs, or secrets on GitHub. In this README, temporary passwords appear as `[temporary password]` and must be stored outside the repository.

---

## Repository Structure

Recommended structure. Save screenshots in `docs/images/` with the names shown in each step.

```text
/
├── README.md
└── docs/
    └── images/
        ├── 01-entra-id.png
        ├── 02-manage-users.png
        ├── 03-users-overview.png
        ├── 04-create-user-basics.png
        ├── 05-create-user-properties.png
        ├── 06-user-created.png
        ├── 07-groups-overview.png
        ├── 08-new-group-engineering-team.png
        ├── 09-select-groups.png
        ├── 10-engineering-team-members.png
        ├── 11-reset-password-button.png
        ├── 12-reset-password-result-REDACTED.png
        ├── 13-disable-account-settings.png
        ├── 14-account-status-disabled.png
        ├── 15-monitoring-sign-in-logs-menu.png
        ├── 16-sign-in-logs-table.png
        └── ... (more screenshots for B.5, B.6, B.7)
```

> 📷 **How to add screenshots:** save each capture in `docs/images/` with the name shown in the step. Do not use Obsidian syntax `![[Pasted image...]]` because GitHub will not render it. On GitHub, use `![Description](docs/images/name.png)`.

---

## Manual Lab

### 1 · Create a User Manually

This manual process shows what the script does behind the scenes. The example uses **Lucia Fernandez**.

**Step 1. Open Microsoft Entra ID.**

From the Azure portal, open Microsoft Entra ID.

[Microsoft Entra ID](docs/images/01-entra-id.png)

**Step 2. Go to Manage > Users.**

In the left menu, open the Users section.

[Manage > Users](docs/images/02-manage-users.png)

**Step 3. Review the user list and click New user.**

[User list](docs/images/03-users-overview.png)

**Step 4. Create the user: Basics tab.**

Create an internal user in your organization. Complete:

- **User principal name:** `lucia.fernandez@diegojose0405gmail.onmicrosoft.com`
- **Mail nickname:** derived from the user principal name.
- **Display name:** `Lucia Fernandez`
- **Password:** generate a temporary password and store it in a safe place. Do not publish it.
- **Account enabled:** on.

Click **Next: Properties**.

[Create new user - Basics](docs/images/04-create-user-basics.png)

**Step 5. Complete the properties: Properties tab.**

Complete the identity and job information:

- **First name:** `Lucia`
- **Last name:** `Fernandez`
- **User type:** `Member`
- **Job title:** `Data Analyst`
- **Company name:** `CyberSec Contract Group`
- **Department:** `Cybersecurity Contractors`
- **Employee ID:** `CTR-2025-1000`
- **Employee type:** `Contractor`
- **Office location:** `Remote`
- **Manager:** add the manager if it already exists.

Click **Review + create** and then **Create**.

[Create new user - Properties](docs/images/05-create-user-properties.png)

**Result:** the user is created and enabled.

[Created user - Lucia Fernandez](docs/images/06-user-created.png)

> ✅ **Check:** in the user profile you should see the User principal name, the Object ID, the creation date, and the status `Enabled`. In this example the creation date is November 14, 2026.

---

### 2 · Create a Group and Assign Membership

**Step 1. Review existing groups.**

Go to **Groups > Overview** and verify that the group you are about to create does not exist yet.

[Groups - Overview](docs/images/07-groups-overview.png)

**Step 2. Create the group.**

Go to **Groups > New group** and complete:

- **Group type:** `Security`
- **Group name:** `Engineering Team`
- **Group description:** `Engineering Team`
- **Membership type:** `Assigned`

Click **Create**.

[New Group - Engineering Team](docs/images/08-new-group-engineering-team.png)

**Step 3. Assign the user to the group.**

Go back to **Users**, open the user profile, go to **Groups > Add memberships**, search for the group, check it, and click **Select**.

In the screenshot below, `Engineering Team` is checked and appears in **Selected groups (1)**. Click **Select** at the bottom to confirm.

[Select groups - Engineering Team checked](docs/images/09-select-groups.png)

**Step 4. Verify the membership.**

Go to **Engineering Team > Members**. You should see 1 group member found: **Lucia Fernandez**, Type `User`, User type `Member`.

[Engineering Team - Members - Lucia Fernandez](docs/images/10-engineering-team-members.png)

> 💡 **Best practice:** always assign permissions through groups, never directly to users. When a user changes roles, you only move them from one group to another and their permissions change automatically.

---

### 3 · Reset Password, Disable, and Re-enable an Account

**Reset password:**

1. Open the user profile.
2. Click **Reset password** in the top toolbar. In the screenshot it is highlighted in red.

[Lucia Fernandez - Reset password button](docs/images/11-reset-password-button.png)

3. Entra ID generates a temporary password. Save it in a safe place. Do not publish it.

[Reset password - Password has been reset - REDACTED](docs/images/12-reset-password-result-REDACTED.png)

> ⚠️ **Important for GitHub:** the original screenshot showed the temporary password in clear text. Use the redacted version above (`12-reset-password-result-REDACTED.png`) for the repository. Do not upload the original screenshot with the visible password.

**Disable an account (Leaver process):**

1. Open the user profile.
2. Go to **Properties > Settings**.
3. Uncheck **Account enabled**, as shown below.
4. Save the changes.

[Properties - Settings - Account enabled unchecked](docs/images/13-disable-account-settings.png)

**Result:** the profile now shows **Account status: Disabled**.

[Account status - Disabled](docs/images/14-account-status-disabled.png)

**Re-enable an account:**

Repeat the same steps, but this time leave **Account enabled** checked and save the changes.

> 🔒 **Golden rule for Leaver:** when an employee leaves, disable their account immediately. Do not wait until the end of the day. That is how you prevent unauthorized access.

---

### 4 · Sign-in Logs: Audit and Monitoring

**Step 1.** Go to **Monitoring > Sign-in logs** in the left menu.

[Monitoring - Sign-in logs menu](docs/images/15-monitoring-sign-in-logs-menu.png)

**Step 2.** In this view you can see sign-in information and filter it as you like: by user, date, status, application, location, or IP address.

The screenshot below shows **User sign-ins (interactive)** with columns for Date, Request ID, User principal name, Application, Status, IP address, Resource, Resource ID, and Conditional Access. The filters at the top are **Add filter**, **Show dates as: UTC**, **Date range: Last 24 hours**, and **Reset filters**.

[Sign-in logs - User sign-ins table](docs/images/16-sign-in-logs-table.png)

> 👀 **Why it matters:** Sign-in logs let you audit who signed in, from where, and whether there were failed attempts. It is your first tool to detect a possible threat.

> 🔒 **Privacy note for GitHub:** the screenshot shows your admin UPN and IP addresses. For a public repository, consider cropping the IP address column or blurring sensitive values before publishing.

---

### 5 · Mover and Leaver: Promotion and Offboarding Simulation

In this section you apply everything you have learned to create users and groups and simulate a role change and an exit.

#### Groups to create

Create these 4 groups:

- `Former Employees`
- `Mid Level Group`
- `New Hire Group`
- `Senior Level Group`

The 4 groups are created as Security groups with Assigned membership:

[Four groups - Former Employees, Mid Level Group, New Hire Group, Senior Level Group](docs/images/17-four-groups.png)

#### Group policies

Configure the policies for each group.

> Important note: for this test, the compliant device policy is disabled, but at enterprise level it is very important to keep it enabled.

The example below shows the policy for **Former Employees**.

In the rule details, the included group is **Former Employees**, the state is **Report-only** (the policy is evaluated but not applied), and the selected controls are **Require multifactor authentication** and **Require device to be marked as compliant**.

[Conditional Access policy - Former Employees - Rule information - MFA and compliant device selected](docs/images/18-group-policies-1.png)

In the **Review and create** step, the plan title is **Former Employees**, the shared condition includes 1 identity, and Rule #1 is **Enabled** with Grant set to **Require multifactor authentication** for all resources.

[Conditional Access policy - Former Employees - Review and create](docs/images/19-group-policies-2.png)

#### Users to create

In **Users**, create these users:

- `Mover`
- `NH1`
- `NH2`
- `SenLeave`
- `Stay`

The user list shows the 5 demo users plus the admin account. All demo users are Type `Member`:

[Users - mover, NH1, NH2, SenLeave, Stay](docs/images/20-mover-leaver-users.png)

#### Initial assignment

Assign each user to their group:

- `Mover` and `Stay` in **Mid Level Group**.
- `SenLeave` in **Senior Level Group**.
- `NH1` and `NH2` in **New Hire Group**.

#### Mover promotion simulation

1. Go to the `Mover` group and remove them from it.

In **Mid Level Group > Members**, 2 group members are found. Select `mover` and click **Remove** in the top toolbar, as highlighted in the screenshot.

[Mid Level Group - Members - mover selected - Remove](docs/images/21-remove-mover.png)

2. Go to **Senior Level Group**. There you will only find `SenLeave`. Remove them right away for their departure and add the `Mover`.

In **Senior Level Group > Members**, the group initially has 0 members. Click **Add members**, check `mover` in the picker, and click **Select** to add them.

[Senior Level Group - Members - Add members - mover selected](docs/images/22-senior-group-change.png)

> Note: in this simulation, `SenLeave` is removed from Senior Level Group as part of the offboarding step before or right after adding `mover`, so the group ends up with the promoted user only.

3. Go to **Former Employees > Members** and add `SenLeave`.

In **Former Employees > Members**, 1 group member is found: **SenLeave**.

[Former Employees - Members - SenLeave](docs/images/23-former-employees-senleave.png)

> ✅ **Expected result:** the `Mover` ends up in **Senior Level Group**, `SenLeave` ends up in **Former Employees**, and their account must be disabled.

---

### 6 · Access Review

The goal of an Access Review is to check that some users no longer need certain permissions or licenses.

#### Lab objectives

- Create a demo group and an enterprise application.
- Assign users to the group.
- Configure an Access Review (Teams + Groups).
- Require justification and auto-apply decisions.
- Complete the review from the user portal.
- Apply results and verify access removal.
- Tear down the environment cleanly.

#### Steps

1. Create a group named `Access Review Demo` and use 3 users: `DEMO1`, `DEMO2`, and `DEMO3`.

The group is created as a Security group with Assigned membership:

[Access Review Demo group](docs/images/24-access-review-group.png)

The 3 demo users are created as Type `Member`:

[Access Review users - DEMO1, DEMO2, DEMO3](docs/images/25-access-review-users.png)

2. Add the users to the group.
3. Go to **Applications**, create an application named `Access-review-demo-app`, and assign it the group `Access Review Demo`.
4. Go to **Identity Governance > Access reviews > New access review** and create a review named `Access_Review_demo2`.
5. Sign in to Microsoft My Access from the Access Review account.

In **My Access > Overview**, the reviewer sees **Your pending actions** with **1 active access review**. Click **Review now** to open it.

[My Access overview - 1 active access review - Review now](docs/images/26-myaccess-1.png)

In the review form for `Access_Review_demo2`, the question is: **Do you still need access to the group 'Access Review Demo'?** The reviewer selects **Yes** and must provide a reason in the **Reason** field before clicking **Submit**.

[Access Review - Do you still need access - Yes - Reason - Submit](docs/images/27-myaccess-2.png)

6. Check the result in **Group > Access Review**.

The progress view shows **3 users** in total:

- **Not reviewed:** 2
- **Approved:** 1
- **Denied:** 0
- **Don't know:** 0

[Access Review - Progress - 3 users - Not reviewed 2, Approved 1](docs/images/28-access-review-result.png)

---

### 7 · Break Glass and Conditional Access

#### Why you need a Break Glass account

Everyone needs a safe path in case they get locked out. If a Conditional Access policy locks you out, you need an account that lets you sign in again to fix the problem.

Create a user `BreakGlassAdmin` for this purpose.

The Break Glass user is created in **Users**. In the list it appears as `BreakGlassAdmin`, Type `Member`, with sign-in identifiers available.

[Users - BreakGlassAdmin](docs/images/29-breakglass-admin.png)

#### Create the policy

Create a Conditional Access policy.

The policy is named `MASTER policy`. In the policy list it appears with State **Report-only**, which means it is evaluated but not enforced yet.

[Conditional Access policies - MASTER policy - Report-only](docs/images/30-conditional-access-policy-1.png)

In the policy details, the assignment is **Users or agents**, with **All users included and specific users excluded**. In the **Exclude** tab, the Break Glass account is selected under **Users and groups**, so it is exempt from the policy.

[MASTER policy - Exclude - Break Glass account excluded](docs/images/31-conditional-access-policy-2.png)

#### Exclude Break Glass

Make sure the `BreakGlass` account is **excluded** from the policy.

> 🔑 **Key point:** the goal is to show the value of Conditional Access and the importance of having an account that lets you get back into the workstation if you get blocked.

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

## Pending Screenshots

When you send the next batch, tell me which step each photo belongs to and I will place it in its spot with its description.

| Step | Status |
| --- | --- |
| B.2 - B.4 | Done: `01` to `16` already placed |
| Section 5 Mover and Leaver | Done: `17` to `23` already placed |
| Section 6 Access Review | Done: `24` to `28` already placed |
| Section 7 Break Glass | Done: `29` to `31` already placed |

All screenshots from `01` to `31` are now placed. There are no pending screenshots.

> All screenshots from `01` to `31` are now placed. The redacted version for the reset password result is `12-reset-password-result-REDACTED.png`. Use that one for GitHub, not the original.

> ⚠️ **Privacy note:** the screenshots in this lab show Object IDs, user principal names, and IP addresses. For a public repository, consider blurring the Object ID column, IP addresses, and any personal UPNs before publishing.

---

## Disclaimer

Organization and writing were assisted by AI, but all steps, explanations, and research were done by Diego Yonoff.

> La organización y redacción fue con ayuda de IA, pero todos los pasos, explicación e investigaciones fueron hechos por Diego Yonoff.
