# Core Portal Lifecycle Procedures

Documentation on the complete TACC ACI-WMA Core v2 Portal lifecycle.

This documentation includes the following:

- An explanation of the portal ecosystem, design decisions and goals driving the evolution of the Core Portal codebase at TACC.
- The procedures used for planning, resourcing, provisioning, configuring and deploying the portal codebase on TACC infrastructure.
- A checklist of explicit, discrete actions to convert into JIRA tasks to track each phase of the lifecycle.
- Instructions on portal customization via use of containers or TAPIS app publishing mechanisms.
- The procedures used for maintenance, backups, archiving and sunsetting of deprecated portal projects.

This documentation should be referenced throughout all phases of a portal's lifecycle.

## Quick Start

**TL;DR** - Take me to the [Lifecycle Procedures Checklist](pages/checklist.md).

## Table of Contents

- [Core Portal Ecosystem](pages/ecosystem.md)
- [Lifecycle Overview](pages/overview.md)
    - [Phase 1: Planning](phase_01)
    - [Phase 2: Code](phase_02)
    - [Phase 3: Builds](phase_03)
    - [Phase 4: Testing](phase_04)
    - [Phase 5: Releases](phase_05)
    - [Phase 6: Deployments](phase_06) (Establishing A Portal)
        - [6A. Administrative Prerequisites](phase_06#6a)
        - [6B. Resource Planning & Allocation](phase_06#6b)
        - [6C. Secrets & Credentials Management](phase_06#6c)
        - [6D. Resource Provisioning & Configuration](phase_06#6d)
        - [6E. Branding & Image Publishing](phase_06#6e)
        - [6F. Deployment Configurations](phase_06#6f)
        - [6G. Deployments](phase_06#6g)
        - [6H. Post Deployment](phase_06#6h)
    - [Phase 7: Operations](phase_07)
        - [7A. Bug Fixes & Patches](phase_07#7a)
        - [7B. Feature Development & Customization](phase_07#7b)
        - [7C. Maintenance & Updates](phase_07#7c)
        - [7D. Backups & Archiving](phase_07#7d)
    - [Phase 8: Monitoring](phase_08)
    - [Phase 9: End of Life](phase_09)
        - [9A. Deprecation](phase_09#9a)
        - [9B. Retirement](phase_09#9b)
- [Lifecycle Procedures Checklist](pages/checklist.md)
- [JIRA Usage](pages/jira-usage.md)
- [Customization](pages/customization.md)
- [Resources](pages/resources.md)
- [Versioning Information](pages/versioning-information.md)
- [Contributors](pages/contributors.md)
- [How to Contribute](pages/how-to-contribute.md)
- [Licensing](pages/licensing.md)


<!-- ### OLD -->
<!--
- [Lifecycle Overview](pages/_old_pages/overview.md)
    - [Phase 1: Administrative Prerequisites & Actions](pages/_old_pages/phase_01.md)
    - [Phase 2: Resource Requests, SSH Certs & CPS Exceptions](pages/_old_pages/phase_02.md)
    - [Phase 3: OAuth Tenants](pages/_old_pages/phase_03.md)
    - [Phase 4: Related Services & Systems](pages/_old_pages/phase_04.md)
    - [Phase 5: Deployment Target Host Provisioning](pages/_old_pages/phase_05.md)
    - [Phase 6: Branding, Content Preparation & Image Publication](pages/_old_pages/phase_06.md)
    - [Phase 7: Secrets & CI/CD Setup](pages/_old_pages/phase_07.md)
    - [Phase 8: Deployments](pages/_old_pages/phase_08.md)
    - [Phase 9: Maintenance](pages/_old_pages/phase_09.md)
    - [Phase 10: Backups & Archiving](pages/_old_pages/phase_10.md)
    - [Phase 11: Sunsetting & Retirement](pages/_old_pages/phase_11.md)
- [Lifecycle Procedures Checklist](pages/_old_pages/checklist.md)
- [JIRA Usage](pages/_old_pages/jira-usage.md)
-->

<!-- ### NEW -->
<!--
- [Lifecycle Overview](pages/_new_pages/overview.md)
    - [Phase 1: Administrative Prerequisites & Actions](pages/_new_pages/phase_01.md)
    - [Phase 2: Resource Requests, SSH Certs & CPS Exceptions](pages/_new_pages/phase_02.md)
    - [Phase 3: OAuth Tenants](pages/_new_pages/phase_03.md)
    - [Phase 4: Related Services & Systems](pages/_new_pages/phase_04.md)
    - [Phase 5: Deployment Target Host Provisioning](pages/_new_pages/phase_05.md)
    - [Phase 6: Branding, Content Preparation & Image Publication](pages/_new_pages/phase_06.md)
    - [Phase 7: Secrets & CI/CD Setup](pages/_new_pages/phase_07.md)
    - [Phase 8: Deployments](pages/_new_pages/phase_08.md)
    - [Phase 9: Maintenance](pages/_new_pages/phase_09.md)
    - [Phase 10: Backups & Archiving](pages/_new_pages/phase_10.md)
    - [Phase 11: Sunsetting & Retirement](pages/_new_pages/phase_11.md)
- [Lifecycle Procedures Checklist](pages/_new_pages/checklist.md)
- [JIRA Usage](pages/_new_pages/jira-usage.md)
-->
