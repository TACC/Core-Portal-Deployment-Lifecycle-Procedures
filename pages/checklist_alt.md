- [Index](../index.md)

---

# Lifecycle Procedures Checklist

<a id="lifecyclePhases"></a>

## Portal Lifecycle Phases

- [Phase 1: Planning](#phase1)
- [Phase 2: Code](#phase2)
- [Phase 3: Builds](#phase3)
- [Phase 4: Testing](#phase4)
- [Phase 5: Releases](#phase5)
- [Phase 6: Deployments](#phase6) (Establishing A Portal)
    - [6A. Administrative Prerequisites](#phase6a)
    - [6B. Resource Planning & Allocation](#phase6b)
    - [6C. Secrets & Credentials Management](#phase6c)
    - [6D. Resource Provisioning & Configuration](#phase6d)
    - [6E. Branding & Image Publishing](#phase6e)
    - [6F. Deployment Configurations](#phase6f)
    - [6G. Deployments](#phase6g)
    - [6H. Post Deployment](#phase6h)
- [Phase 7: Operations](#phase7)
    - [7A. Bug Fixes & Patches](#phase7a)
    - [7B. Feature Development & Customization](#phase7b)
    - [7C. Maintenance & Updates](#phase7c)
    - [7D. Backups & Archiving](#phase7d)
- [Phase 8: Monitoring](#phase8)
- [Phase 9: End of Life](#phase9)
    - [9A. Deprecation](#phase9a)
    - [9B. Retirement](#phase9b)

---

<a id="phaseActions"></a>

## Lifecycle Phase Actions

<a id="phase1"></a>

### [Phase 1: Planning](phase_01)

- **Action:** [TBD](#tbd)

---

<a id="phase2"></a>

### [Phase 2: Code](phase_02)

- **Action:** [TBD](#tbd)

---

<a id="phase3"></a>

### [Phase 3: Builds](phase_03)

- **Action:** [TBD](#tbd)

---

<a id="phase4"></a>

### [Phase 4: Testing](phase_04)

- **Action:** [TBD](#tbd)

---

<a id="phase5"></a>

### [Phase 5: Releases](phase_05)

- **Action:** [TBD](#tbd)

---

<a id="phase6"></a>

### [Phase 6: Deployments](phase_06)

#### [6A. Administrative Prerequisites](phase_06#6a)

- **Action:** [Identify the portal project PI.](#action1)
- **Action:** [Identify or establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities.](#action3)
- **Action:** [Identify Portal Project TAS GID associated with the portal allocation.](#action4)
- **Action:** [Ensure the correct users have admin and access to the `TAS` project.](#action5)
- **Action:** [Identify the WMA developers responsible for portal setup, deployment and maintenance.](#action2)
- **Action:** [Ensure WMA developers responsible for portal setup have access to requires resources.](#action7)
- **Action:** [Identify and acquire the official "vanity" URL to be used by the portal.](#action6)

---

#### [6B. Resource Planning & Allocation](phase_06#6b)

#### [Host VM Requests]()

- **Action:** [Request the deployment target host VMs for `PPRD`, `PROD`, `DEV`, etc. via KB.](#action1)

#### [SSL Certificates]()

- **Action:** [Request SSL Certificates for each requested host VM via KB.](#action4)

#### [WSO2 Tenant Request]()

- **Action:** [Select the Tenant Type for the portal (shared or dedicated).](#action1)
  - [Shared Tenant](#shared)
  - [Dedicated Tenant](#dedicated)
- **Action:** [Request a dedicated WSO2 tenant for `TAPIS` access.](#action2)
- **Action:** [Install portal service applications on the dedicated tenant.](#action3)

#### [CPS Exceptions](#cps)

- **Action:** [Have a CPS exception made for the `PROD` vanity domain name URL.](#action7)

---

#### [6C. Secrets & Credentials Managements](phase_06#6c)

#### [Credentials Management](#management)

- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for admin: PROJECTNAME ADMIN.](#action1)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS.](#action1)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal.](#action2)

#### [Create Credentials](#credentials)

##### [Tenant](#)

- **Action:** [Create a TACC Tenant OAuth client for each host VM.](#action3)
- **Action:** [Configure TACC Tenant long lived token for each host VM.](#action5)

##### [PostgreSQL](#)

- **Action:** [Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM Portal.](#action5)
- **Action:** [Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM CMS.](#action6)

##### [ElasticSearch](#)

- **Action:** [Create ElasticSearch Credentials in the WMA ES Cluster for each host VM.](#action7)
- **Action:** [Create ElasticSearch Indeces in the WMA ES Cluster for each host VM Portal and host VM CMS.](#action7)

##### [Verification, reCAPTCHA & Analytics](#)

- **Action:** [Generate a new Google Analytics property ID for the PROD vanity domain name.](#action2)
- **Action:** [Generate a new Google Site Verification token for the PROD vanity domain name.](#action3)
- **Action:** [Generate a new reCAPTCHA code for the PROD vanity domain name.](#action4)

#### [Document Secrets](#document-secrets)

- **Action:** [Populate UT Stache with the secret values for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS.](#action1)
- **Action:** [Populate UT Stache with the secret values for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal.](#action2)

#### [Prepare Settings](#prepare-settings)

- **Action:** [Create a `secrets.py` file for the django CMS container on each host VM.](#action5)
- **Action:** [Create a `settings_secret.py` file for the django portal container on each host VM.](#action6)
- **Action:** [Create a `rabbitmq.env` file for each host VM.](#action9)

---

#### [6D. Resource Provisioning & Configuration](phase_06#6d)

#### [Host Provisioning](#host-provisioning)

_Note: Repeat these steps for each deployment target host._

- **Action:** [Generate the `dhparam.pem` file on the deployment target host.](#action1)
- **Action:** [On the deployment target host create the user `portal`.](#action2)
- **Action:** [Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.](#action3)
- **Action:** [Nginx SSL Certs Configuration for containers.](#action4)
- **Action:** [Install host dependencies.](#action5)
- **Action:** [Add the `portal` user to the (new) `docker` group.](#action6)
- **Action:** [Create deployment directories for the Camino workflow in each deployment host VM.](#action7)
- **Action:** [Clone Camino into each deployment host VM.](#action9)
- **Action:** [Request that NSO grant the user `portal` SSH access from the Jenkins Deployer VM IP Address into each deployment host VM.](#action11)

#### [Placing Secrets](#placing-secrets)

- **Action:** [SCP `secrets.py` into each deployment host VM.](#action11)
- **Action:** [SCP `settings_secret.py` into each deployment host VM.](#action12)
- **Action:** [SCP `rabbitmq.env` into each deployment host VM.](#action15)

#### [CI/CD Jobs](#cicd-jobs)

- **Action:** [Configure the Portal Project Jenkins CI job.](#action17)

#### [Backend Systems](#systems)

- **Action:** [Create Default Storage Systems for the project.](#action18)
- **Action:** [Create Default Execution Systems for the project.](#action20)
- **Action:** [Setup a Community Data Project.](#action22)
- **Action:** [Setup a Public Data Project.](#action23) _(Optional)_ 

---

#### [6E. Branding & Image Publishing](phase_06#6e)

- **Action:** [Setup the custom branding and navigation bar in Core-CMS-Resources.](#action1)
- **Action:** [Generate & Publish the Custom Project CMS Image on Dockerhub.](#action2)
s
---

#### [6F. Deployment Configurations](phase_06#6f)

- **Action:** [Update the Core-Portal-Deployments repo with correct docker image tag values for the CMS and Portal containers.](#action2)

---

#### [6G. Deployments](phase_06#6g)

- **First Deployment**: [New portals.](#fd)
- **Reqular Deployment**: [Established portals.](#rd)

#### [First Deployment](#fdi)

- **Action:** [Deploy the Portal via Jenkins CI job on the target host system.](#action1)
- **Action:** [SSH into the deployment target host and become the user `portal`.](#action2)
- **Action:** [Complete the container setup.](#action3)
- **Action:** [Create an index page in the CMS.](#action4)

#### [Regular Deployment](#rdi)

- **Action:** [Deploy the Portal via Jenkins CI job to each target host system.](#action5)

---

#### [6H. Post Deployment](phase_06#6h)

- **Action:** [Run the ES Indexing management command against each deployed target host VM.](#action7)
- **Action:** [Schedule a QA Review for each deployed target host VM.](#action8)

---

<a id="phase7"></a>

### [Phase 7: Operations](phase_07)

#### [7A. Bug Fixes & Patches](phase_07#7a)

- **Action:** [TBD](#tbd)

---

#### [7B. Feature Development & Customization](phase_07#7b)

- **Action:** [TBD](#tbd)

---

#### [7C. Maintenance & Updates](phase_07#7c)

- **Action:** [TBD](#tbd)

---

#### [7D. Backups & Archiving](phase_07#7d)

- **Action:** [TBD](#tbd)

---

<a id="phase8"></a>

### [Phase 8: Monitoring](phase_08)

- **Action:** [TBD](#tbd)

---

<a id="phase9"></a>

### [Phase 9: End of Life](phase_09)

#### [9A. Deprecation](phase_09#9a)

- **Action:** [TBD](#tbd)

---

#### [9B. Retirement](phase_09#9b)

- **Action:** [TBD](#tbd)

---

- [Index](../index.md)
