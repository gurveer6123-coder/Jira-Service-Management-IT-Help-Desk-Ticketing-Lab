# Jira Service Management – IT Help Desk Ticketing Lab

## Project Overview

This project demonstrates a simulated **IT Help Desk / Service Desk environment** built using **Jira Service Management (JSM)**.

The purpose of this lab was to practice realistic Level 1 IT Support workflows, including ticket intake, triage, troubleshooting, customer communication, internal documentation, access requests, escalation to Level 2, resolution, queue management, reporting, and SLA monitoring.

The lab contains three primary support scenarios:

1. Office Wi-Fi connectivity issue
2. Temporary local administrator access request
3. Departmental shared-drive access issue with L1-to-L2 escalation

A separate Level 2 subtask was also created to demonstrate escalation and technician-to-technician communication.

> **Note:** This is a simulated lab environment created for hands-on IT support practice and portfolio development. The users, troubleshooting scenarios, approvals, and escalation workflow were created for training purposes.

---

## Technologies and Concepts Used

- Jira Service Management
- IT Service Management (ITSM)
- Ticket lifecycle management
- Service requests
- Ticket queues
- SLA monitoring
- Jira reporting
- Windows networking
- IPv4 addressing
- DHCP troubleshooting
- Command Prompt
- Active Directory concepts
- AD security groups
- Shared-folder permissions
- Share and NTFS permission concepts
- Least privilege
- Access management
- L1-to-L2 escalation

---

# 1. IT Support Help Desk Environment

A dedicated Jira Service Management service space named:

**IT Support Help Desk**

was created using the IT Service Management template.

The environment included:

- Customer request portal
- Agent workspace
- Request types
- Ticket queues
- Priorities
- Assignees
- Ticket statuses
- Internal notes
- Customer replies
- SLAs
- Subtasks
- Reports


---

# 2. Ticket 1 – Office Wi-Fi Connectivity Issue

## Scenario

A user reported that their work device could not connect to the office Wi-Fi.

The request was categorized as:

- **Request Type:** Get IT help
- **Priority:** Medium
- **Assignee:** Harry
- **Status:** In Progress

The purpose of this ticket was to practice basic L1 network troubleshooting and customer communication.

---

## Initial Triage

The ticket was assigned to the technician and moved from **Waiting for support** to **In Progress**.

An internal troubleshooting plan was documented.

The planned troubleshooting included:

- Verify Wi-Fi is enabled
- Confirm Airplane mode is disabled
- Confirm the correct wireless SSID
- Forget and reconnect to the wireless network
- Verify network credentials
- Check IPv4 configuration
- Check the default gateway
- Determine whether the problem is device-specific or network-related

![Wi-Fi Ticket Triage](Ticket%20System/02-Ticket-Triage-In-Progress.png)

---

## Customer Communication

The customer was contacted through Jira using **Reply to customer**.

The user was asked to:

- Verify Wi-Fi was enabled
- Confirm Airplane mode was disabled
- Forget the office Wi-Fi network
- Reconnect using their credentials
- Report any error messages

This demonstrated the difference between Jira's two communication methods:

**Internal Note**  
Used for technical documentation and communication between IT staff.

**Reply to Customer**  
Used for information that should be visible to the end user.

![Customer Communication](Ticket%20System/03-Customer-Communication.png)

---

## IP Configuration Investigation

The customer confirmed that the basic Wi-Fi troubleshooting did not resolve the issue.

The user was then asked to run:

```cmd
ipconfig
```

The Wi-Fi adapter showed an address in the:

```text
169.254.x.x
```

range with no default gateway.

A `169.254.x.x` APIPA address indicated that the workstation had not successfully obtained a normal IPv4 address from DHCP.

The customer was instructed to run:

```cmd
ipconfig /release
ipconfig /renew
```

After renewing the DHCP lease, the workstation received:

```text
IPv4 Address: 192.168.10.47
```

A valid default gateway was also assigned.

The customer confirmed that Wi-Fi and network connectivity were restored.

![Customer Resolution Confirmation](Ticket%20System/04-Customer-Resolution-Confirmation.png)

---

## Ticket Resolution

The final internal documentation recorded the cause and solution.

**Root Cause:**  
The workstation failed to obtain a valid DHCP lease.

**Resolution:**  
The DHCP lease was released and renewed, allowing the device to receive a valid IPv4 address and default gateway.

**Customer Verification:**  
The customer confirmed that Wi-Fi connectivity and network access were restored.

The ticket was then moved to **Resolved**.

![Wi-Fi Ticket Resolved](Ticket%20System/05-Ticket-Resolved.png)

---

# 3. Ticket 2 – Temporary Local Administrator Access

## Scenario

A user requested temporary local administrator access to install approved IT troubleshooting software.

This ticket was treated as an **access/service request** rather than a technical incident.

The purpose of this scenario was to practice:

- Business justification
- Approval requirements
- Least privilege
- Temporary elevated access
- Access removal
- Security documentation

---

## Access Request Review

Before granting administrator access, an internal note documented the planned validation steps.

The request required:

- Verification that the software was approved
- Confirmation of authorized approval
- Restriction of administrator access to the required workstation
- Temporary access only
- Removal of elevated privileges after installation

The request was placed into a pending state while authorization was considered.

![Admin Access Awaiting Approval](Ticket%20System/06-Admin-Access-Awaiting-Approval.png)

---

## Approval and Access Provisioning

The lab simulated receiving authorization for the temporary administrator request.

The access was documented as:

- Limited to the assigned workstation
- Temporary
- Required only for approved IT troubleshooting software
- Subject to removal after the installation was completed

The request demonstrated the principle of **least privilege**, where administrative rights should only be granted when required and for the minimum necessary period.

![Admin Access Approved](Ticket%20System/07-Admin-Access-Resolved.png)

---

## Access Removal and Resolution

After the simulated software installation was completed, the user confirmed that administrator access was no longer required.

The final technician actions included:

- Confirm approved software was installed successfully
- Remove temporary administrator access
- Return the user to standard permissions
- Confirm no further action was required

The customer was informed that the access had been removed and the request was resolved.

![Admin Access Request Resolved](Ticket%20System/08-Admin-Access-Request-Resolved.png)

---

# 4. Ticket 3 – Departmental Shared Drive Access Denied

## Scenario

A user reported receiving:

```text
Access Denied
```

when attempting to access a departmental shared network drive.

The user had previously been able to access the resource, and other network services were still functioning.

This scenario was designed to practice:

- L1 troubleshooting
- Windows/domain troubleshooting concepts
- AD security-group investigation
- Permission troubleshooting
- L1-to-L2 escalation
- Escalation documentation

---

## Initial L1 Triage

The initial L1 troubleshooting plan included:

- Verify network connectivity
- Confirm the correct shared-drive path
- Verify whether the drive was still mapped
- Disconnect and remap the drive
- Confirm the correct domain account was being used
- Consider AD security-group membership
- Determine whether share or NTFS permissions required further investigation

No permissions were changed during initial troubleshooting.

![Shared Drive Initial Triage](Ticket%20System/09-Shared-Drive-Initial-Triage.png)

---

## L1 Troubleshooting Completed

The following checks were completed:

- Network connectivity was working
- The user was authenticated with the correct domain account
- The correct shared-drive path was being used
- The drive was disconnected and remapped
- Other network resources were accessible
- The Access Denied error remained

The results indicated that the issue was likely related to:

- Active Directory security-group membership
- Share permissions
- NTFS permissions

At this point, the problem was outside the normal scope of L1 troubleshooting.

Escalation to Level 2 / Systems Administration was required.

![L1 Troubleshooting Completed](Ticket%20System/10-Shared-Drive-L2-Escalation.png)

---

# 5. L1 to L2 Escalation

A separate subtask was created:

**L2 review – shared drive permissions**

The escalation contained the troubleshooting already completed by Level 1 so that Level 2 would not have to repeat the same work.

The escalation included:

### L1 Troubleshooting Completed

- Network connectivity verified
- Correct domain credentials confirmed
- Correct shared-drive path verified
- Shared drive disconnected and remapped
- Other network resources tested successfully

### Requested L2 Investigation

Level 2 was asked to review:

- Active Directory security-group membership
- Effective share permissions
- Effective NTFS permissions

![L2 Escalation](Ticket%20System/11-Shared-Drive-L2-Escalation.png)

---

# 6. Level 2 Investigation and Resolution

The simulated Level 2 investigation determined that the user was missing the required Active Directory security-group membership for the departmental shared drive.

The user was restored to the appropriate security group.

The user was then instructed to refresh their authentication session by signing out and signing back in.

After doing so, the customer confirmed that the shared drive was accessible again.

The final documentation recorded:

**Root Cause:**  
Missing required Active Directory security-group membership.

**Resolution:**  
The user was restored to the appropriate security group and their authentication session was refreshed.

**Customer Verification:**  
The user confirmed successful access to the shared drive.

![Shared Drive Escalation Resolved](Ticket%20System/12-Shared-Drive-Escalation-Resolved.png)

---

# 7. L1 and L2 Communication Workflow

This lab also demonstrated how communication may be handled between support tiers.

The workflow used was:

```text
Customer
   ↓
Level 1 Support
   ↓
Level 2 / Systems Administration
   ↓
Level 1 Support
   ↓
Customer
```

Level 2 technical findings were documented using **internal notes**.

Level 1 remained responsible for translating the technical findings into clear customer-facing communication.

This prevents unnecessary technical details from being sent directly to users while maintaining a complete technical record for the IT team.

---

# 8. Custom Jira Queue

A custom Jira queue named:

**Recently Resolved Tickets**

was created.

The queue displayed the completed lab work:

- `ITSD-1` – Office Wi-Fi connectivity issue
- `ITSD-2` – Temporary administrator access request
- `ITSD-3` – Departmental shared-drive Access Denied
- `ITSD-4` – L2 shared-drive permissions review

The custom queue demonstrated how support teams can organize tickets according to specific operational requirements.

![Recently Resolved Tickets Queue](Ticket%20System/13-Recently-Resolved-Tickets-Queue.png)

---

# 9. Jira Service Desk Reporting

Jira Service Management reporting was used to review completed service-desk activity.

The **Requests resolved** report displayed completed work during the lab period.

The report showed four completed work items, including the three primary tickets and the Level 2 subtask.

![Requests Resolved Report](Ticket%20System/14-Requests-Resolved-Report.png)

---

# 10. SLA Monitoring

Service Level Agreements (SLAs) help IT teams measure whether support requests are being handled within agreed service targets.

The lab environment tracked:

- Time to first response
- Time to resolution

The Jira SLA report showed:

**Time to First Response:** `100%`

**Time to Resolution:** `100%`

These figures represent the performance of the simulated lab tickets during the selected reporting period.

![SLA Success Rate](Ticket%20System/15-SLA-Success-Rate.png)

---

# 11. Ticket Lifecycle Practiced

The complete ticket lifecycle practiced in this lab was:

```text
Customer submits request
        ↓
Waiting for Support
        ↓
Ticket triage
        ↓
Request categorization
        ↓
Priority assignment
        ↓
Agent assignment
        ↓
In Progress
        ↓
Troubleshooting
        ↓
Internal documentation
        ↓
Customer communication
        ↓
Pending / Waiting for information
        ↓
Additional troubleshooting
        ↓
Escalation if required
        ↓
Technical resolution
        ↓
Customer verification
        ↓
Resolved
```

---

# 12. Internal Notes vs Customer Replies

Understanding the difference between internal and external communication is an important service-desk skill.

## Internal Notes

Internal notes were used for:

- Troubleshooting documentation
- Diagnostic results
- Root-cause analysis
- Technician-to-technician communication
- Escalation information
- Security-related changes
- Resolution details

These notes are intended for IT staff and are not normally visible to the customer.

## Reply to Customer

Customer replies were used for:

- Troubleshooting instructions
- Requests for additional information
- Status updates
- Resolution updates
- Confirmation requests
- Ticket closure communication

This allows the service desk to maintain detailed technical records while keeping customer communication professional and understandable.

---

# 13. Escalation Process

The shared-drive scenario demonstrated that Level 1 should perform appropriate troubleshooting before escalating a ticket.

The escalation included:

- Description of the problem
- Troubleshooting already completed
- Results of the tests
- Suspected technical cause
- Requested Level 2 action

Providing this information reduces duplicated troubleshooting and allows Level 2 technicians to continue the investigation efficiently.

---

# 14. Security and Access Management Concepts

The administrator-access request demonstrated several important security principles.

### Least Privilege

Users should only receive the permissions necessary to perform their required task.

### Approval

Elevated access should be authorized before it is granted.

### Temporary Privilege Elevation

Administrative permissions should only remain active for the required duration.

### Scope Limitation

Access should be restricted to the required device or system whenever possible.

### Access Removal

Temporary elevated privileges should be removed once the approved task is complete.

### Documentation

Security-related access changes should be documented in the ticket for accountability and auditing.

---

# 15. Technical Troubleshooting Practiced

## Networking

The Wi-Fi scenario included:

```cmd
ipconfig
ipconfig /release
ipconfig /renew
```

Concepts practiced included:

- IPv4 addressing
- DHCP
- APIPA
- Default gateways
- Wireless connectivity
- Network troubleshooting

## Active Directory

The shared-drive scenario included concepts related to:

- Domain authentication
- AD security groups
- User access
- Group membership
- Shared-folder authorization

## File Permissions

The escalation scenario included investigation of:

- Share permissions
- NTFS permissions
- Effective user access
- Security-group-based authorization

---

# 16. Skills Demonstrated

This project demonstrates hands-on familiarity with:

- Jira Service Management
- ITSM workflows
- IT Help Desk operations
- Service Desk ticketing
- Ticket lifecycle management
- Ticket triage
- Ticket categorization
- Request types
- Priority assignment
- Ticket assignment
- Internal notes
- Customer communication
- Professional support documentation
- Windows networking troubleshooting
- IPv4 troubleshooting
- DHCP troubleshooting
- APIPA identification
- Command Prompt networking commands
- Active Directory concepts
- Security-group troubleshooting
- Shared-drive troubleshooting
- Share and NTFS permission concepts
- Access management
- Least privilege
- Temporary administrator access
- Approval workflows
- L1 troubleshooting
- L1-to-L2 escalation
- Jira subtasks
- Custom queues
- SLA monitoring
- Service Desk reporting
- Root-cause documentation
- Customer verification
- Ticket resolution

---

# 17. Key Takeaways

This lab demonstrated that effective IT support involves more than simply fixing a technical problem.

A support technician must also:

1. Understand the user's issue
2. Gather relevant information
3. Categorize the request correctly
4. Set an appropriate priority
5. Assign responsibility
6. Document troubleshooting clearly
7. Communicate professionally with the customer
8. Protect sensitive internal technical information
9. Recognize when escalation is required
10. Provide Level 2 with useful troubleshooting information
11. Document the root cause
12. Verify that the customer is satisfied with the resolution
13. Close the ticket correctly
14. Monitor service performance through queues and reports
15. Understand SLA requirements

---

# Project Outcome

The Jira Service Management lab successfully demonstrated three complete IT support scenarios and one Level 2 escalation subtask.

The completed lab included:

- End-to-end incident troubleshooting
- Service/access request handling
- Security approval workflow
- Temporary privilege elevation
- Customer communication
- Internal support documentation
- L1-to-L2 escalation
- Active Directory access troubleshooting
- Subtask management
- Root-cause documentation
- Customer verification
- Custom Jira queue creation
- Jira reporting
- SLA monitoring

This project provides practical evidence of familiarity with the workflows commonly used by **IT Support, Help Desk, Service Desk, Desktop Support, and Junior Systems Administration teams**.

---

## Project Status

**Completed ✅**
