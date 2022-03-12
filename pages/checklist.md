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
    - [7A. Feature Development & Customization](#phase7a)
    - [7B. Bug Fixes & Patches](#phase7b)
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

<a id="phase6a"></a>

#### [6A. Administrative Prerequisites](phase_06#6a)

- **Action:** [Identify the portal project PI.](phase_06#6a-action-01)
- **Action:** [Identify or establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities.](phase_06#6a-action-02)
- **Action:** [Identify Portal Project TAS GID associated with the portal allocation.](phase_06#6a-action-03)
- **Action:** [Ensure the correct users have admin and access to the `TAS` project.](phase_06#6a-action-04)
- **Action:** [Identify the WMA developers responsible for portal setup, deployment and maintenance.](phase_06#6a-action-05)
- **Action:** [Ensure WMA developers responsible for portal setup have access to requires resources.](phase_06#6a-action-06)
- **Action:** [Identify and acquire the official "vanity" URL to be used by the portal.](phase_06#6a-action-07)

---

<a id="phase6b"></a>

#### [6B. Resource Planning & Allocation](phase_06#6b)

#### [Host VM Requests](phase_06#6b-vm-requests)

- **Action:** [Request the deployment target host VMs for `PPRD`, `PROD`, `DEV`, etc. via KB.](phase_06#6b-action-01)

#### [SSL Certificates](phase_06#6b-ssl-certs)

- **Action:** [Request SSL Certificates for each requested host VM via KB.](phase_06#6b-action-02)

#### [WSO2 Tenant Request](phase_06#6b-tenant-requests)

- **Action:** [Select the Tenant Type for the portal (shared or dedicated).](phase_06#6b-action-03)
- **Action:** [Request a dedicated WSO2 tenant for `TAPIS` access.](phase_06#6b-action-04)
- **Action:** [Install portal service applications on the dedicated tenant.](phase_06#6b-action-05)

#### [CPS Exceptions](phase_06#6b-cps)

- **Action:** [Have a CPS exception made for the `PROD` vanity domain name URL.](phase_06#6b-action-06)

---

<a id="phase6c"></a>

#### [6C. Secrets & Credentials Managements](phase_06#6c)

#### [Credentials Management](phase_06#6c-credentials-management)

- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for admin: PROJECTNAME ADMIN.](phase_06#6c-action-01)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS.](phase_06#6c-action-02)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal.](phase_06#6c-action-03)

#### [Create Credentials](phase_06#6c-create-credentials)

##### [Tenant](phase_06#6c-tenant)

- **Action:** [Create a TACC Tenant OAuth client for each host VM.](phase_06#6c-action-04)
- **Action:** [Configure TACC Tenant long lived token for each host VM.](phase_06#6c-action-05)

##### [PostgreSQL](phase_06#6c-postgresql)

- **Action:** [Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM Portal.](phase_06#6c-action-06)
- **Action:** [Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM CMS.](phase_06#6c-action-07)

##### [ElasticSearch](phase_06#6c-elastic-search)

- **Action:** [Create ElasticSearch Credentials in the WMA ES Cluster for each host VM.](phase_06#6c-action-08)
- **Action:** [Create ElasticSearch Indeces in the WMA ES Cluster for each host VM Portal and host VM CMS.](phase_06#6c-action-09)

##### [Web Services](phase_06#6c-web-services)

- **Action:** [Generate a new Google Analytics property ID for the PROD vanity domain name.](phase_06#6c-action-10)
- **Action:** [Generate a new Google Site Verification token for the PROD vanity domain name.](phase_06#6c-action-11)
- **Action:** [Generate a new reCAPTCHA code for the PROD vanity domain name.](phase_06#6c-action-12)

#### [Document Secrets](phase_06#6c-document-secrets)

- **Action:** [Populate UT Stache with the secret values for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS.](phase_06#6c-action-13)
- **Action:** [Populate UT Stache with the secret values for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal.](phase_06#6c-action-14)

#### [Prepare Settings](phase_06#6c-prepare-settings)

- **Action:** [Create a `secrets.py` file for the django CMS container on each host VM.](phase_06#6c-action-15)
- **Action:** [Create a `settings_secret.py` file for the django portal container on each host VM.](phase_06#6c-action-16)
- **Action:** [Create a `rabbitmq.env` file for each host VM.](phase_06#6c-action17)

---

<a id="phase6d"></a>

#### [6D. Resource Provisioning & Configuration](phase_06#6d)

#### [Host Provisioning](phase_06#6d-host-provisioning)

_Note: Repeat these steps for each deployment target host._

- **Action:** [Generate the `dhparam.pem` file on the deployment target host.](phase_06#6d-action-01)
- **Action:** [On the deployment target host create the user `portal`.](phase_06#6d-action-02)
- **Action:** [Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.](phase_06#6d-action-03)
- **Action:** [Nginx SSL Certs Configuration for containers.](phase_06#6d-action-04)
- **Action:** [Install host dependencies.](phase_06#6d-action-05)
- **Action:** [Add the `portal` user to the (new) `docker` group.](phase_06#6d-action-06)
- **Action:** [Create deployment directories for the Camino workflow in each deployment host VM.](phase_06#6d-action-07)
- **Action:** [Clone Camino into each deployment host VM.](phase_06#6d-action-08)
- **Action:** [Request that NSO grant the user `portal` SSH access from the Jenkins Deployer VM IP Address into each deployment host VM.](phase_06#6d-action-09)

#### [Placing Secrets](phase_06#6d-placing-secrets)

- **Action:** [SCP `secrets.py` into each deployment host VM.](phase_06#6d-action-10)
- **Action:** [SCP `settings_secret.py` into each deployment host VM.](phase_06#6d-action-11)
- **Action:** [SCP `rabbitmq.env` into each deployment host VM.](phase_06#6d-action-12)

#### [CI/CD Jobs](phase_06#6d-cicd-jobs)

- **Action:** [Configure the Portal Project Jenkins CI job.](phase_06#6d-action-13)

#### [Backend Systems](phase_06#6d-systems)

- **Action:** [Create Default Storage Systems for the project.](phase_06#6d-action-14)
- **Action:** [Create Default Execution Systems for the project.](phase_06#6d-action-15)
- **Action:** [Setup a Community Data Project.](phase_06#6d-action-16)
- **Action:** [Setup a Public Data Project.](phase_06#6d-action-17) _(Optional)_ 

---

<a id="phase6e"></a>

#### [6E. Branding & Image Publishing](phase_06#6e)

- **Action:** [Setup the custom branding and navigation bar in Core-CMS-Resources.](phase_06#6e-action-01)
- **Action:** [Generate & Publish the Custom Project CMS Image on Dockerhub.](phase_06#6e-action-02)

---

<a id="phase6f"></a>

#### [6F. Deployment Configurations](phase_06#6f)

- **Action:** [Update the Core-Portal-Deployments repo with correct docker image tag values for the CMS and Portal containers.](phase_06#6f-action-01)

---

<a id="phase6g"></a>

#### [6G. Deployments](phase_06#6g)

#### [6G1. First Deployment](phase_06#6g1) (New portals)

- **Action:** [Deploy the Portal via Jenkins CI job on the target host system.](phase_06#6g1-action-01)
- **Action:** [SSH into the deployment target host and become the user `portal`.](phase_06#6g1-action-02)
- **Action:** [Complete the container setup.](phase_06#6g1-action-03)
- **Action:** [Create an index page in the CMS.](phase_06#6g1-action-04)

#### [6G2. Regular Deployment](phase_06#6g2) (Existing portals)

- **Action:** [Deploy the Portal via Jenkins CI job to each target host system.](phase_06#6g2-action-01)

---

<a id="phase6h"></a>

#### [6H. Post Deployment](phase_06#6h)

- **Action:** [Run the ES Indexing management command against each deployed target host VM.](phase_06#6h-action-01)
- **Action:** [Schedule a QA Review for each deployed target host VM.](phase_06#6h-action-02)

---

<a id="phase7"></a>

### [Phase 7: Operations](phase_07)

<a id="phase7a"></a>

#### [7A. Feature Development & Customization](phase_07#7a)

- **Action:** [TBD](#tbd)

---

<a id="phase7b"></a>

#### [7B. Bug Fixes & Patches](phase_07#7b)

- **Action:** [TBD](#tbd)

---
<a id="phase7c"></a>

#### [7C. Maintenance & Updates](phase_07#7c)

- **Action:** [TBD](#tbd)

---

<a id="phase7d"></a>

#### [7D. Backups & Archiving](phase_07#7d)

- **Action:** [TBD](#tbd)

---

<a id="phase8"></a>

### [Phase 8: Monitoring](phase_08)

- **Action:** [TBD](#tbd)

---

<a id="phase9"></a>

### [Phase 9: End of Life](phase_09)

<a id="phase9a"></a>

#### [9A. Deprecation](phase_09#9a)

- **Action:** [TBD](#tbd)

---

<a id="phase9b"></a>

#### [9B. Retirement](phase_09#9b)

- **Action:** [TBD](#tbd)

---

- [Index](../index.md)
