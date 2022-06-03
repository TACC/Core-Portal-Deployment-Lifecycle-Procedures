- [Index](../index.md)

---

# Lifecycle Overview

The primary focus of this documentation is on Phases 6 through 8 (_Deployments_, _Operations_ and _Monitoring_). Phases 1 through 5 (_Planning_, _Code_, _Builds_, _Testing_, _Releases_) will only contain documentation that is globally relevant to all `Core-*` projects and codebases. The majority of the documentation detailing these procedures is located in other repositories (links to each of which can be found under the [resources](resources#top) page). The procedural documentation for Phase 9 is currently being developed.

## Lifecycle Phases

<!-- TODO: Update the anchor tag naming for all Phase specific pages to drop the `-action. instead` use `phase_06_A#6A-01` (not `phase_06_A#6a-action-01`) to reduce some verbosity. -->

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

### Developer Notes

- Each **SubPhase** (_6A-6H, 7A-7D, 9A-B_) is an aggregation of steps called _Actions_. 
- Each **Action** is a discrete task that must be completed to fulfill the _SubPhase_ objective.
- See the [Core Portal Ecosystem](ecosystem.md) page for an explanation of the design decisions and goals driving the evolution of the Core Portal codebases.
- See the [Customization](customization.md) page for instructions on how to extend the portal architecture with additional containers or published TAPIS applications.

---

- [Index](../index.md)
