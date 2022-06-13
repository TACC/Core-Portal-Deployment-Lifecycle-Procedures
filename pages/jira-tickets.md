<a id="top"></a>

- [Index](../index.md)

---

# JIRA Tickets

## Key Concepts

There are a few key concepts to understand in order to make use of the suggestions in this document.

- Several portal lifecycle phases are comprised of multiple _SubPhases_, indicated by a number and letter combination (e.g. 6A, 7B, 9A).
- Each **SubPhase** is an aggregation of steps called _Actions_.
- Each **Action** is a discrete task that must be completed to fulfill the SubPhase objective.

### Tracking Phase 6 Deployment Tasks

When deploying a new portal (Subphases 6A - 6H), it can be difficult to track the many individual tasks and their status, especially if the tasks are assigned to multiple team members who are working in parallel or across multiple portal projects.

In order to facilitate the tracking of the deployment procedures, we recommend the following strategy:

1. Create a JIRA **Task** under the portal's JIRA project for each _SubPhase_ of the CPLP Phase 6 Deployment:
   - _6A Administrative Prerequisites_
   - _6B Resource Planning & Allocation_
   - _6C Secrets & Credentials Management_
   - _6D Resource Provisioning & Configuration_
   - _6E Branding & Image Publishing_
   - _6F Deployment Configurations_
   - _6G Deployments_
   - _6H Post Deployment_
2. Create a JIRA **Task** for each _Action_ listed under each _SubPhase_.
3. Link each _Action_ **Task** to the parent _SubPhase_ **Task** in JIRA (e.g. Using the  _is a subtask of_ link type).
4. Track the progress of each _Action_ **Task** to determine progress on the related parent _SubPhase_ **Task**.
5. Deployment will be succesful when all _Subphase_ **Tasks** have been completed successfully.

<a class="inline-navlink-page-top" href="#top">Back to Top</a>

---

- [Index](../index.md)
