# AWS IAM Privilege Escalation Detection & Prevention

## Overview

This project demonstrates AWS IAM privilege escalation risks, detection techniques, and remediation workflows using AWS IAM and AWS CloudTrail.

The project simulates dangerous IAM permission configurations that allow a low-privileged user to indirectly gain administrative access through privilege escalation paths.

---

## AWS Services Used

* AWS IAM
* AWS CloudTrail

---

## Security Concepts Demonstrated

* IAM Privilege Escalation
* IAM Trust Policy Abuse
* Least Privilege Principle
* IAM Policy Review
* CloudTrail Auditing
* IAM Security Remediation

---

## Privilege Escalation Techniques Demonstrated

| Technique             | Description                                                                  |
| --------------------- | ---------------------------------------------------------------------------- |
| CreateUser Escalation | Created a new IAM user and attached AdministratorAccess                      |
| Trust Policy Hijack   | Modified IAM role trust relationship to allow unauthorized AssumeRole access |

---

# Escalation Technique 1 — CreateUser Escalation

## Risk

A low-privileged IAM user with dangerous IAM permissions was able to create a new IAM user and attach AdministratorAccess.

## Dangerous Permissions

* iam:CreateUser
* iam:AttachUserPolicy

## Security Impact

This demonstrates how users without direct administrative access can still create persistent admin backdoor accounts.

---

# Escalation Technique 2 — Trust Policy Hijack

## Risk

An IAM user modified an IAM role trust relationship to allow unauthorized AssumeRole access.

## Dangerous Permission

* iam:UpdateAssumeRolePolicy

## Security Impact

This demonstrates how modifying IAM trust relationships can allow users to temporarily assume highly privileged IAM roles.

---

## Detection & Auditing

CloudTrail Event History was used to detect:

* CreateUser events
* IAM trust policy modifications
* Suspicious IAM activity

---

## Remediation

The following remediation actions were implemented:

* Removed dangerous IAM permissions
* Detached privilege escalation policies
* Restored original IAM trust relationships
* Applied least privilege access

---

## Key Learnings

* Certain IAM permissions can indirectly become admin-equivalent
* Trust relationships are critical security boundaries in AWS
* Least privilege is essential in IAM design
* CloudTrail provides auditing visibility for IAM changes
* Privilege escalation risks often come from misconfigured IAM permissions

---

## Outcome

Successfully demonstrated AWS IAM privilege escalation techniques, security auditing, and remediation workflows using AWS IAM and CloudTrail.
