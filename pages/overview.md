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

## Checklist Phases

There are several phases in the portal deployment lifecycle. Each phase is an aggregation of steps required to prepare for subsequent phases. This is the complete list of steps (referred to as a `Task`) needed to prepare, setup, configure and deploy a CEP v2 Core Portal.

- [Phase 1: Portal Administrative Prerequisite Actions](#phase1)
- [Phase 2: Portal Resource Requests, SSH Certs & CPS Exceptions](#phase2)
- [Phase 3: Portal Tenant Setup](#phase3)
  - [Option 3A - Shared Tenant (Default)](#phase3optA)
  - [Option 3B - Dedicated Tenant](#phase3optB)
  - [Get a CPS Exception on the Tenant](#phase3cps)
- [Phase 4: Portal Related Services & Systems Setup](#phase4)
- [Phase 5: Portal Deployment Target Host Provisioning](#phase5)
- [Phase 6: Portal Branding, Content Preparation & Image Publication](#phase6)
- [Phase 7: Portal Deployment Workflow Setup](#phase7)
- [Phase 8: Portal Deployments](#phase8)
  - [Initial Deployment Workflow](#phase8IDW)
  - [Regular Deployment Workflow](#phase8RDW)
- [Phase 9: Portal Maintenance](#phase9)
- [Phase 10: Portal Backup & Archiving](#phase10)
- [Phase 11: Portal Sunsetting & Retirement](#phase11)
- [Custom Portal Development (Optional)](#custom)
- [Other Actions](#other)

## Phase Descriptions











---

[Return to Index](../index.md)
