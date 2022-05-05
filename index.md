# Core Portal Lifecycle Procedures

Documentation on the complete TACC ACI-WMA Core v2 Portal lifecycle.

This documentation includes the following:

- A detailed explanation of the portal ecosystem, design decisions and goals driving the evolution of the Core Portal codebase at TACC during development, testing and release phases.
- The complete list of procedures for planning, resourcing, provisioning, configuring and deploying the portal codebase on TACC infrastructure.
- The procedures used for maintenance, backups, archiving and sunsetting of deprecated portal projects.
- A checklist of explicit, discrete actions to convert into JIRA tasks in order to track progress during the deployment phase of the portal lifecycle.
- Instructions on how to customize the portal branding.
- Instructions on how to add custom portal capabilities via the use of containers or TAPIS.
- Instructions on how to report bugs or contribute to the codebase.

This documentation should be referenced throughout all phases of a portal's lifecycle.

### Important

**This is living documentation that will be reviewed and updated regularly.**

The primary focuses of this documentation is on Phases 6 through 8 (Deployments, Operations and Monitoring). Phases 1 through 5 (Planning, Code, Builds, Testing, Releases) will only contain documentation that is globally relevant to all `Core-*` projects and codebases. The majority of the relevant documentation for these procedures is already located within the relevant code repositories (links to each can be found under the [resources](pages/resources#top) page). The procedural documentation for Phase 9 is currently being developed and will be added at a later time.

## Table of Contents

- [Core Portal Ecosystem](pages/ecosystem.md)
- [Lifecycle Overview](pages/overview.md)
  - [Phase 1: Planning](pages/phase_01)
  - [Phase 2: Code](pages/phase_02)
  - [Phase 3: Builds](pages/phase_03)
  - [Phase 4: Testing](pages/phase_04)
  - [Phase 5: Releases](pages/phase_05)
  - [Phase 6: Deployments](pages/phase_06) (Establishing A Portal)
    - [6A. Administrative Prerequisites](pages/phase_06#6a)
    - [6B. Resource Planning & Allocation](pages/phase_06#6b)
    - [6C. Secrets & Credentials Management](pages/phase_06#6c)
    - [6D. Resource Provisioning & Configuration](pages/phase_06#6d)
    - [6E. Branding & Image Publishing](pages/phase_06#6e)
    - [6F. Deployment Configurations](pages/phase_06#6f)
    - [6G. Deployments](pages/phase_06#6g)
    - [6H. Post Deployment](pages/phase_06#6h)
  - [Phase 7: Operations](pages/phase_07)
    - [7A. Feature Development & Customization](pages/phase_07#7a)
    - [7B. Bug Fixes & Patches](pages/phase_07#7b)
    - [7C. Maintenance & Updates](pages/phase_07#7c)
    - [7D. Backups & Archiving](pages/phase_07#7d)
  - [Phase 8: Monitoring](pages/phase_08)
  - [Phase 9: End of Life](pages/phase_09)
    - [9A. Deprecation](pages/phase_09#9a)
    - [9B. Retirement](pages/phase_09#9b)
- [JIRA Usage](pages/jira-usage.md)
- [Customization](pages/customization.md)
- [Resources](pages/resources.md)
- [Versioning Information](pages/versioning-information.md)
- [Contributors](pages/contributors.md)
- [How to Contribute](pages/how-to-contribute.md)
- [Licensing](pages/licensing.md)
