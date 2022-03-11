- [Index](../index.md)

---

# Lifecycle Overview

This is a list of all _Phases_ in the TACC ACI-WMA Core v2 Portal lifecycle. Each _Phase_ is an aggregation of steps (called _Actions_) that must be completed to succesfully fulfill the _Phase_ objectives.

**Lifecycle Phases**

## [Phase 1: Planning]()

## [Phase 2: Code]()

## [Phase 3: Builds]()

## [Phase 4: Testing]()

## [Phase 5: Releases]()

## [Phase 6: Deployment]() (Establishing A Portal)

### [6A. Administrative Prerequisites]()

- **Action:** [Identify the portal project PI.](#action1)
- **Action:** [Identify or establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities.](#action3)
- **Action:** [Identify Portal Project TAS GID associated with the portal allocation.](#action4)
- **Action:** [Ensure the correct users have admin and access to the `TAS` project.](#action5)
- **Action:** [Identify the WMA developers responsible for portal setup, deployment and maintenance.](#action2)
- **Action:** [Ensure WMA developers responsible for portal setup have access to requires resources.](#action7)
- **Action:** [Identify and acquire the official "vanity" URL to be used by the portal.](#action6)

### [6B. Resource Planning & Allocation]()

#### [Host VM Requests]()

- **Action:** [Request the deployment hosts for `PPRD` via KB.](#action1)
- **Action:** [Request the deployment hosts for `PROD` via KB.](#action2)
- **Action:** [If needed, request the deployment hosts for DEV via KB.](#action3)

#### [SSL Certificates]()

- **Action:** [Request SSL Certificates for the `PPRD` deployment host via KB.](#action4)
- **Action:** [Request SSL Certificates for the `PROD` deployment host via KB.](#action5)
- **Action:** [If needed, request SSL Certificates for the `DEV` deployment host via KB.](#action6)

#### [WSO2 Tenant Request]()

- **Action:** [Select Tenant Type for the portal (shared or dedicated).](#action1)
  - [Shared Tenant](#shared)
  - [Dedicated Tenant](#dedicated)
- **Action:** [Request a dedicated WSO2 tenant for `TAPIS` access.](#action2)
- **Action:** [Install portal service applications on the dedicated tenant.](#action3)

#### [CPS Exceptions](#cps)

- **Action:** [Have a CPS exception made for the `PROD` vanity domain name.](#action7)

### [6C. Secrets & Credentials Management]()

#### [Credentials Management](#management)

- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for PROJECTNAME ADMIN.](#action1)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for the PROJECTNAME PPRD CMS.](#action1)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for the PROJECTNAME PPRD Portal.](#action2)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for the PROJECTNAME PROD CMS.](#action3)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for the PROJECTNAME PROD Portal.](#action4)

#### [Create Credentials](#credentials)

##### [Tenant](#)

- **Action:** [Create a TACC Tenant OAuth client for Pre-production.](#action3)
- **Action:** [Configure TACC Tenant long lived token for Pre-production.](#action5)

- **Action:** [Create a TACC Tenant OAuth client for Production.](#action4)
- **Action:** [Configure TACC Tenant long lived token for Production.](#action6)

##### [PostgreSQL](#)

- **Action:** [Create PreProd Portal Database Credentials & Database in WMA PostgreSQL Cluster.](#action5)
- **Action:** [Create Production Portal Database Credentials & Database in WMA PostgreSQL Cluster.](#action6)

##### [ElasticSearch](#)

- **Action:** [Create Pre-production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.](#action7)
- **Action:** [Create Production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.](#action8)

##### [Verification, reCAPTCHA & Analytics](#)

- **Action:** [Generate Google Analytics property ID.](#action2)
- **Action:** [Generate Google Site Verification token.](#action3)
- **Action:** [Generate reCAPTCHA code.](#action4)

#### [Document Secrets](#document-secrets)

- **Action:** [Populate UT Stache with the secret values for the PPRD CMS.](#action1)
- **Action:** [Populate UT Stache with the secret values for the PPRD Portal.](#action2)
- **Action:** [Populate UT Stache with the secret values for the PROD CMS.](#action3)
- **Action:** [Populate UT Stache with the secret values for the PROD Portal.](#action4)

#### [Prepare Settings](#prepare-settings)

- **Action:** [Create `secrets.py` for the PPRD django CMS container.](#action5)
- **Action:** [Create `settings_secret.py` for the PPRD django portal container.](#action6)
- **Action:** [Create `secrets.py` for the PROD django CMS container.](#action7)
- **Action:** [Create `settings_secret.py` for the PROD django portal container.](#action8)
- **Action:** [Create `rabbitmq.env` for the PPRD host.](#action9)
- **Action:** [Create `rabbitmq.env` for the PROD host.](#action10)

### [6D. Resource Provisioning & Configuration](#6d)

#### [Host Provisioning](#host-provisioning)

_Note: Repeat these steps for each deployment target host._

- **Action:** [Generate the `dhparam.pem` file on the deployment target host.](#action1)
- **Action:** [On the deployment target host create the user `portal`.](#action2)
- **Action:** [Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.](#action3)
- **Action:** [Nginx SSL Certs Configuration for containers.](#action4)
- **Action:** [Install host dependencies.](#action5)
- **Action:** [Add the `portal` user to the (new) `docker` group.](#action6)
- **Action:** [Create deployment directories for the Camino workflow in the PPRD deployment host.](#action7)
- **Action:** [Create deployment directories for the Camino workflow in the PROD deployment host.](#action8)
- **Action:** [Clone Camino into PPRD deployment host.](#action9)
- **Action:** [Clone Camino into PROD deployment host.](#action10)
- **Action:** [Request SSH access for user `portal` from the Jenkins VM IP Address into the PPRD host from NSO.](#action11)
- **Action:** [Request SSH access for user `portal` from the Jenkins VM IP Address into the PROD host from NSO.](#action12)

#### [Placing Secrets](#placing-secrets)

- **Action:** [SCP `secrets.py` into the PPRD host.](#action11)
- **Action:** [SCP `settings_secret.py` into the PPRD host.](#action12)
- **Action:** [SCP `secrets.py`  into the PROD host.](#action13)
- **Action:** [SCP `settings_secret.py` into the PROD host.](#action14)
- **Action:** [SCP `rabbitmq.env` into the PPRD host.](#action15)
- **Action:** [SCP `rabbitmq.env` into the PROD host.](#action16)

#### [CI/CD Jobs](#cicd-jobs)

- **Action:** [Configure the Portal Project Jenkins CI job.](#action17)

#### [Backend Systems](#systems)

- **Action:** [Create Pre-production Portal Default Storage Systems.](#action18)
- **Action:** [Create Production Portal Default Storage Systems.](#action19)
- **Action:** [Create PPRD Portal Default Execution Systems.](#action20)
- **Action:** [Create PROD Portal Default Execution Systems.](#action21)
- **Action:** [Setup Community Data Project.](#action22)
- **Action:** [Setup Public Data Project (if requested).](#action23)

### [6D. Branding, Image Publishing & Deployment Configurations]()

- **Action:** [Setup the custom branding and navigation bar in Core-CMS-Resources.](#action1)
- **Action:** [Generate & Publish Custom CMS Image on Dockerhub.](#action2)
- **Action:** [Update the Core-Portal-Deployments repo with correct docker image tag values for the CMS and Portal.](#action2)

### [6E. Deployment Actions](#deployments)

- **First Deployment**: [New portals.](#fd)
- **Reqular Deployment**: [Established portals.](#rd)

#### [First Deployment](#fdi)

- **Action:** [Deploy the Portal via Jenkins CI job on the target host system.](#action1)
- **Action:** [SSH into the deployment target host and promote to user `portal`.](#action2)
- **Action:** [Complete the container setup.](#action3)
- **Action:** [Create index page in CMS.](#action4)

#### [Regular Deployment](#rdi)

- **Action:** [Deploy the Portal via Jenkins CI job to the target host system.](#action5)
- **Action:** [Schedule a QA Review for the deployment target host.](#action6)

### [6F. Post Deployment](#pda)

- **Action:** [Run the ES Indexing management command against the deployment target host.](#action7)
- **Action:** [Schedule a QA Review for the deployment target host.](#action8)

## [Phase 7: Operations](phase_07.md)

### [7A. Bug Fixes & Patches](#bug-fixes-patches)

- **Action:** [TBD](#)
- **Action:** [TBD](#)

### [7B. Feature Development & Customization]()

- **Action:** [TBD](#)
- **Action:** [TBD](#)

### [7C. Maintenance & Updates](#maintenance)

- **Action:** [TBD](#)
- **Action:** [TBD](#)

### [7D. Backups & Archiving](#backups-archiving)

- **Action:** [TBD](#)
- **Action:** [TBD](#)

### [7E. EOL Deprecation & Retirement](phase_11.md)

- **Action:** [TBD](#)
- **Action:** [TBD](#)

## [Phase 8: Monitoring](phase_08.md)

- **Action:** [TBD](#)
- **Action:** [TBD](#)

---

See the [Lifecycle Procedures Checklist](checklist.md) page for a comprehensive list of every _Action_ in all _Phases_ of the portal lifecycle.

See the [Customization](customization.md) page for instructions on how to extend the portal architecture with additional containers or published TAPIS applications.

See the [Core Portal Ecosystem](ecosystem.md) page for an explanation of the design decisions and goals driving the evolution of the Core Portal codebase.

---

- [Index](../index.md)
