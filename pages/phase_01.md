- [Index](../index.md) > [Overview](overview.md)

---

<a id="phase1"></a>

# Phase 1: Administrative Prerequisite Actions

## Objective

Describe the objectives of this phase of the lifecycle.

<a id="actions"></a>

## Administrative Prerequisite Actions

- **Action:** [Identify the portal project PI.](#action1)
- **Action:** [Identify the WMA developers responsible for portal setup, deployment and maintenance.](#action2)
- **Action:** [Identify/establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities.](#action3)
- **Action:** [Identify Portal Project TAS GID associated with the portal allocation.](#action4)
- **Action:** [Ensure the correct users have admin and access to the `TAS` project.](#action5)
- **Action:** [Identifyacquire the official "vanity" URL to be used by the portal.](#action6)
- **Action:** [Ensure WMA developers responsible for portal setup have access to requires resources.](#action7)

---

<a id="instructions"></a>

## Action Instructions

---

### Phase 1: Portal Administrative Prerequisite Actions

---

<a id="action1"></a>

**Action: Identify the portal project PI**

Description pending.

---

<a id="action2"></a>

**Action: Identify the WMA developers responsible for portal setup, deployment and maintenance**

Description pending.

---

<a id="action3"></a>

**Action: Identify/establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities**

Any new portal being established must be charged against a project that is officially recognized by TACC. Additionally, any computational or storage resources used by the portal on behalf of its users must be charged against a resource allocation associated with the project. TACC users who qualify for PI status can initiate new projects in the TACC User Portal and request resource allocations.

_Procedure_

- Create a TACC user account in the TACC User Portal (TUP): https://portal.tacc.utexas.edu/home
- New users account request information can be found here: https://portal.tacc.utexas.edu/account-request
- Determining PI eligibility information can be found here: https://portal.tacc.utexas.edu/allocations-overview#eligibility
  - _Note that in order to be PI Eligible your account will have to be approved by TACC administrators._
- Once a PI eligible TACC user account has been established, complete the setup steps for pairing MFA with the new account: https://portal.tacc.utexas.edu/tutorials/multifactor-authentication
- Once the PI user account is completely setup, login to the TUP and review the information on allocation types: https://portal.tacc.utexas.edu/tutorials/managing-allocations
- From the TUP, the PI User can create a new project, administrate the project and request an allocation for the project to utilize against TACC resources.
- TACC staff (with access permission) can verify account status by accessing the TACC Accounting System (TAS): https://tas.tacc.utexas.edu
- Once the allocation request is approved, the remaining procedures for establishing a new portal can commence.

---

<a id="action4"></a>

**Action: Identify Portal Project TAS GID associated with the portal allocation**

Description pending.

---

<a id="action5"></a>

**Action: Ensure the correct users have admin and access to the `TAS` project**

Description pending.

---

<a id="action6"></a>

**Action: Identifyacquire the official "vanity" URL to be used by the portal (e.g. - `www.vanityurlfornewportal.com`)**

Portal projects should request a domain name for their portal to expose for internet access by its users.

- Example. If the portal is for the Exascale Science Project, request a domain like exascale-science.org or exascalescience.org or exasci.org

Acquiring a new domain is not an immediate process. New domains first have to be purchased using funding from the project account. Once the domain has been purchased, ISO has to approve transfer of domain control over to TACC for association with the portal and the SSL certificates used to secure access to the system. Once the domain name is under TACC control, the SSL certificates required by the portal can be generated and placed into the host VMs. After the certs are in position on the host VM systems, the deployment process can proceed.

To request a new domain be acquired for a portal, submit a new ticket to the TACC consulting system under the Technology Infrastructure (TI) queue: https://consult.tacc.utexas.edu/Ticket/Create.html?Queue=1

DNS propagation status can be checked using this site: https://dnschecker.org/#CNAME/

---

<a id="action7"></a>

**Action: Ensure WMA developers responsible fopr portal setup have access to requires resources.**

In order to succesfully deploy a Core v2 Portal, you will need the following:

- Access to these Resources:
    - TBD
    - TBD

- Access to these Repositories:
    - TBD
    - TBD

- Access to these account credentials:
    - TACC ACI-WMA Portal Service Account
    - TBD

---

- [Index](../index.md) > [Overview](overview.md)
