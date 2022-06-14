<a id="top"></a>

- [Index](../index.md) > [DevOps Lifecycle](devops.md) > [Phase 6](phase_06.md)

---

<a id="actions"></a>

# Phase 6A: Administrative Prerequisites

<a id="6a-01"></a>

### Identify the Portal Project PI

TACC users who qualify for PI status can initiate new projects in the TACC User Portal and request resource allocations.

1. Create a TACC user account in the [TACC User Portal](https://portal.tacc.utexas.edu/home) (TUP).
   - There are few [steps](https://www.tacc.utexas.edu/use-tacc/getting-started) that both users and developers are required to take before they can start their work.
2. Review the new user [account request](https://portal.tacc.utexas.edu/account-request) procedures.
   - Once a user's account is approved, users must set up [MFA](https://portal.tacc.utexas.edu/tutorials/multifactor-authentication) via the TACC User Portal using an approved authenticator app.
3. Review the procedures for determining [PI eligibility](https://portal.tacc.utexas.edu/allocations-overview#eligibility).
4. Once a PI eligible TACC user account has been established, be sure to complete the steps for [MFA pairing](https://portal.tacc.utexas.edu/tutorials/multifactor-authentication).

<a id="6a-02"></a>

### Identify or Establish a TAS Project/Allocation

TACC portals are charged against a project that is officially recognized by the TACC Accounting System (TAS). Any computational or storage resources used by the portal on behalf of its users will be be charged against an allocation associated with the project. The project and allocation is also used to provide user access controls, job submissions and resource usage accounting activities.

1. Once the PI user account is completely setup, login to TUP and review the information on [allocation types](https://portal.tacc.utexas.edu/tutorials/managing-allocations).
2. From TUP, the PI User can create a new project, request an allocation for the project to utilize against TACC resources and administrate the project.
   - Users can request allocation(s) on the system(s) most applicable to their work.
   - See the [TACC User Guides](https://portal.tacc.utexas.edu/user-guides) for details on all TACC systems.
   - Each machine will have a section describing the machine's characteristics, queue structure, how to interact with the TACC storage systems from that machine (including tips for transferring data to and from the system), etc.
3. TACC staff with appropriate access permissions can verify account status by accessing the [TAS](https://tas.tacc.utexas.edu).
4. Once the allocation request is approved, the remaining procedures for establishing a new portal can commence.

<a id="6a-03"></a>

### Identify the TAS Project GID for the Portal Allocation

TACC staff with appropriate access permissions can verify the project TAS GID by accessing [TAS](https://tas.tacc.utexas.edu).

1. Login to the [TAS](https://tas.tacc.utexas.edu) portal.
2. Select the **Projects** tab.
3. Enter the project name and click the **search** link.
4. Select the specific project you are examining by clicking the **details** link in the results list.
5. Look under the **project information** section for the **default gid** value.

<a id="6a-04"></a>

### Ensure the Correct Users are Added to the TAS Project

Once the PI has established the portal project and an allocation for resource accounting, they can add users (with active TACC user accounts) to the project via the [TACC User Portal](https://portal.tacc.utexas.edu/home).

<a id="6a-05"></a>

### Identify the WMA Developer(s) Administrating the Portal

The TACC ACI-WMA Leadership Team will assign WMA team members to each portal project as is determined appropriate.

<a id="6a-06"></a>

### Verify Developer Access to Required Resources

Once WMA developers have been assigned to a portal project, they should verify that they have access to the accounts and systems required to establish and deploy the new portal project.

<a id="6a-07"></a>

### Identify the Public URL for the Portal

Portal projects can secure a custom domain name for their portal or they can use a tacc subdomain (e.g. `portalname.tacc.utexas.edu`). Acquiring a new domain is not an immediate process.  New domains first have to be purchased using funding from the project account. Once the domain has been purchased, the university ISO has to approve transfer of domain control over to TACC for association with the portal and generating the SSL certificates used to secure access to the system. This process normally takes 3-4 weeks.

<a class="inline-navlink-page-top" href="#top">Back to Top</a>

---

- [Index](../index.md) > [DevOps Lifecycle](devops.md) > [Phase 6](phase_06.md)
