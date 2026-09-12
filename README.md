# Jira Service Management – IT Help Desk Ticketing Lab

## Overview

This project demonstrates a hands-on IT Help Desk environment created using **Jira Service Management (JSM)**.

The lab was designed to simulate real-world Level 1 IT Support workflows, including:

- Ticket creation and triage
- Request categorization
- Priority management
- Ticket assignment
- Customer communication
- Internal technician documentation
- Troubleshooting
- Pending / waiting states
- Access request approval workflows
- Least-privilege administration
- L1 to L2 escalation
- Subtasks
- Resolution documentation
- Custom queues
- SLA tracking
- Service desk reporting

Three primary support scenarios were completed from initial request through resolution.

> **Note:** This is a simulated lab environment created for hands-on IT support practice and portfolio development.

---

# Technologies Used

- Jira Service Management
- IT Service Management (ITSM)
- Windows networking concepts
- DHCP troubleshooting
- Active Directory concepts
- Security groups
- Share and NTFS permission concepts
- Service Level Agreements (SLAs)

---

# Lab Environment

A dedicated Jira Service Management service project was created:

**Service Desk:** `IT Support Help Desk`

The environment included Jira Service Management features such as:

- Customer portal
- Agent workspace
- Queues
- Request types
- Internal notes
- Customer replies
- Ticket statuses
- Priorities
- SLAs
- Subtasks
- Reports

![IT Support Help Desk](Ticket%20System/01-IT-Support-Help-Desk.png)

---

# Ticket 1 – Office Wi-Fi Connectivity Issue

## Scenario

A user reported that their work device could not connect to the office Wi-Fi.

The ticket was categorized as:

- **Request Type:** Get IT help
- **Priority:** Medium
- **Assignee:** IT Support
- **Initial Status:** Waiting for support

The ticket was assigned and moved into **In Progress** for troubleshooting.

---

## Initial Triage

The initial troubleshooting plan included:

- Verify Wi-Fi is enabled
- Verify Airplane mode is disabled
- Confirm the correct SSID
- Forget and reconnect to the wireless network
- Verify credentials
- Check IP configuration
- Check the default gateway
- Determine whether the issue was device-specific or network-related

Internal notes were used to document technical troubleshooting that should not be visible to the customer.

![Ticket Triage](Ticket%20System/02-Ticket-Triage-In-Progress.png)

---

## Customer Communication

A customer-facing response was sent requesting that the user:

1. Confirm Wi-Fi was enabled.
2. Confirm Airplane mode was disabled.
3. Forget and reconnect to the office Wi-Fi.
4. Report any connection errors.

This demonstrated the difference between:

- **Internal Notes** – technician-only documentation
- **Reply to Customer** – customer-facing communication

![Customer Communication](Ticket%20System/03-Customer-Communication.png)

---

## DHCP Troubleshooting

The customer reported an IPv4 address in the `169.254.x.x` range with no default gateway.

This indicated that the workstation had not successfully received an IPv4 address from DHCP.

The user was instructed to run:

```cmd
ipconfig /release
ipconfig /renew
