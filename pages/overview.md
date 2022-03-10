# Core Portal Deployment Procedure Overview

[Return to Index](../index.md)

## Checklist Purpose

- Used for new Portal planning, provisioning, setup, configuration and deployment.
- For all new CEP v2 portal deployments, this checklist should be duplicated (and renamed appropriately) in Confluence.
- Convert each task on the checklist into a JIRA ticket under the correct JIRA Project, Epic Sprint, etc.
- Document the JIRA ticket ID for each task on the checklist as you create the ticket.
- Add the JIRA ticket integration plugin in the Confluence tracking document for the given portal.

The JIRA integration will display for each ticketed task:

- The link to the relevant JIRA ticket
- Completion status
- Due date
- The reporter/assigned dev for each task
- The priority of the task
- Other task details as populated in JIRA.

## Deployment Phases

There are several phases in the portal deployment lifecycle. Each phase is an aggregation of steps required to prepare for subsequent phases. This is the complete list of steps (referred to as a `Task`) needed to prepare, setup, configure and deploy a CEP v2 Core Portal.

**TODO: Link to phase details pages.** 

- [Phase 1: Portal Administrative Prerequisite Actions](phase-01.md)
- [Phase 2: Portal Resource Requests, SSH Certs & CPS Exceptions](phase-02.md)
- [Phase 3: Portal Tenant Setup](phase-03.md)
  - [Option 3A - Shared Tenant (Default)](phase-03.md/#phase3optA)
  - [Option 3B - Dedicated Tenant](phase-03.md/#phase3optB)
  - [Get a CPS Exception on the Tenant](phase-03.md/#phase3cps)
- [Phase 4: Portal Related Services & Systems Setup](phase-04.md)
- [Phase 5: Portal Deployment Target Host Provisioning](phase-05.md)
- [Phase 6: Portal Branding, Content Preparation & Image Publication](phase-06.md)
- [Phase 7: Portal Deployment Workflow Setup](phase-07.md)
- [Phase 8: Portal Deployments](phase-08.md)
  - [Initial Deployment Workflow](phase-08.md/#phase8IDW)
  - [Regular Deployment Workflow](phase-08.md/#phase8RDW)
- [Phase 9: Portal Maintenance](phase-09.md)
- [Phase 10: Portal Backup & Archiving](phase-10.md)
- [Phase 11: Portal Sunsetting & Retirement](phase-11.md)
- [Custom Portal Development (Optional)](customization.md)

For a detailed list of all Tasks required to deploy a portal, see the [Deployment Procedures Checklist](pages/checklist.md)].

---

[Return to Index](../index.md)
