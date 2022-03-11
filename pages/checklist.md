- [Index](../index.md)

---

# Lifecycle Procedures Checklist

<a id="lifecyclePhases"></a>

## Portal Lifecycle Phases

- [Phase 1: Administrative Prerequisite Actions](#phase1)
- [Phase 2: Resource Requests, SSH Certs & CPS Exceptions](#phase2)
- [Phase 3: OAuth Tenants](#phase3)
- [Phase 4: Related Services & Systems](#phase4)
- [Phase 5: Deployment Target Host Provisioning](#phase5)
- [Phase 6: Branding, Content Preparation & Image Publication](#phase6)
- [Phase 7: Secrets & CI/CD Jobs](#phase7)
- [Phase 8: Deployments](#phase8)
- [Phase 9: Maintenance](#phase9)
- [Phase 10: Backups & Archiving](#phase10)
- [Phase 11: Sunsetting & Retirement](#phase11)

---

<a id="phaseActions"></a>

## Lifecycle Phase Actions

<a id="phase1"></a>

### _[Phase 1: Administrative Prerequisite Actions](phase_01)_

- **Action:** [Identify the portal project PI.](phase_01#phase1action1)
- **Action:** [Identify the WMA developers responsible for portal setup, deployment and maintenance.](phase_01#phase1action2)
- **Action:** [Identify/establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities.](phase_01#phase1action3)
- **Action:** [Identify Portal Project TAS GID associated with the portal allocation.](phase_01#phase1action4)
- **Action:** [Ensure the correct users have admin and access to the `TAS` project.](phase_01#phase1action5)
- **Action:** [Identifyacquire the official "vanity" URL to be used by the portal.](phase_01#phase1action6)
- **Action:** [Ensure WMA developers responsible for portal setup have access to requires resources.](phase_01#phase1action7)

---

<a id="phase2"></a>

### _Phase 2: Resource Requests, SSH Certs & CPS Exceptions_

- **Action:** Request the deployment hosts for `PPRD` via KB.
- **Action:** Request the deployment hosts for `PROD` via KB.
- **Action:** If needed, request the deployment hosts for DEV via KB (only used in cases of custom development on a CEP fork).
- **Action:** Request SSL Certificates for the `PPRD` deployment host via KB (required to deploy the portal codebase).
- **Action:** Request SSL Certificates for the `PROD` deployment host via KB (required to deploy the portal codebase).
  - _Note: This step **cannot** be completed until the vanity URL is controlled by TACC NSO and UT EIS._
- **Action:** If used, request SSL Certificates for the `DEV` deployment host via KB (required to deploy the portal codebase).

---

<a id="phase3"></a>

### _Phase 3: OAuth Tenant_

- **Action:** Select Tenant Type (shared or dedicated) for the portal (dedicated tenants require additional actions, the shared tenant is already setup).

#### _Dedicated Tenant_

- **Action:** Request a dedicated `WSO2 tenant` for `TAPIS` access (requires coordination with `ACI-CIC`).
- **Action:** Install portal service applications on the dedicated tenant (zippy, compress, extract, pems).

#### _Tenant Configuration_

- **Action:** Create a TACC Tenant OAuth client for Pre-production.
- **Action:** Create a TACC Tenant OAuth client for Production.
- **Action:** Configure TACC Tenant long lived token for Pre-production.
- **Action:** Configure TACC Tenant long lived token for Production.

#### _CPS Exception_

- **Action:** Have a CPS exception made for the `PROD` vanity domain name.

---

<a id="phase4"></a>

### _Phase 4: Related Services & Systems Setup_

- **Action:** Establish a new UT Stache entry to store project credentials and secret settings (`https://stache.utexas.edu`).
- **Action:** Add Google Analytics property ID.
- **Action:** Generate Google Site Verification token.
- **Action:** Generate reCAPTCHA code.
- **Action:** Create PreProd Portal Database Credentials & Database in WMA PostgreSQL Cluster.
- **Action:** Create Production Portal Database Credentials & Database in WMA PostgreSQL Cluster.
- **Action:** Create Pre-production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.
- **Action:** Create Production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.
- **Action:** Create Pre-production Portal Default Storage Systems.
- **Action:** Create Production Portal Default Storage Systems.

---

<a id="phase5"></a>

### _Phase 5: Deployment Target Host Provisioning_

_Note: Repeat these steps for both PPRD & PROD._

- **Action:** Generate the `dhparam.pem` file on the deployment target host.
- **Action:** On the deployment target host (as `root`), create the user `portal`.
- **Action:** Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.
- **Action:** Nginx SSL Certs Configuration for containers.
- **Action:** Install host dependencies.
- **Action:** Add the `portal` user to the (new) group `docker`: `sudo usermod -aG docker portal`
- **Action:** Create deployment directories for the Camino workflow in the PPRD deployment host.
- **Action:** Create deployment directories for the Camino workflow in the PROD deployment host.
- **Action:** Clone Camino into PPRD deployment host.
- **Action:** Clone Camino into PROD deployment host.
- **Action:** Request SSH access for user `portal` from the Jenkins VM IP Address into the PPRD host from NSO.
- **Action:** Request SSH access for user `portal` from the Jenkins VM IP Address into the PROD host from NSO.

---

<a id="phase6"></a>

### _Phase 6: Branding, Content Preparation & Image Publication_

- **Action:** Setup the custom branding and navigation bar in Core-CMS-Resources.
- **Action:** Generate & Publish Custom CMS Image on Dockerhub.

---

<a id="phase7"></a>

### _Phase 7: Secrets & CI/CD Jobs_

- **Action:** Populate UT Stache with the secret values specific to the PPRD CMS.
- **Action:** Populate UT Stache with the secret values specific to the PPRD Portal.
- **Action:** Populate UT Stache with the secret values specific to the PROD CMS.
- **Action:** Populate UT Stache with the secret values specific to the PROD Portal.
- **Action:** Create `secrets.py` for the PPRD django CMS container.
- **Action:** SCP `secrets.py` into the PPRD host `/opt/portal/Camino/conf/cms/` subdir.
- **Action:** Create `settings_secret.py` for the PPRD django portal container.
- **Action:** SCP `settings_secret.py` into the PPRD host `/opt/portal/Camino/conf/portal/` subdir.
- **Action:** Create `secrets.py` for the PROD django CMS container.
- **Action:** SCP `secrets.py`  into the PROD host `/opt/portal/Camino/conf/cms/` subdir.
- **Action:** Create `settings_secret.py` for the PROD django portal container.
- **Action:** SCP `settings_secret.py` into the PROD host `/opt/portal/Camino/conf/portal/` subdir.
- **Action:** Create `rabbitmq.env` (can be the same for all hosts).
- **Action:** SCP `rabbitmq.env` into the PPRD host `/opt/portal/Camino/conf/rabbitmq/` subdir.
- **Action:** SCP `rabbitmq.env` into the PROD host `/opt/portal/Camino/conf/rabbitmq/` subdir.
- **Action:** Configure the Portal Project Jenkins CI job.

---

<a id="phase8"></a>

### _Phase 8: Deployments_

- **Initial Deployment Workflow**: For brand new portals, complete these procedures for all deployment targets (e.g. PROD, PPRD).
- **Reqular Deployment Workflow**: Follow these procedures for existing portals.

#### _Initial Deployment Workflow_

- **Action:** Deploy the Portal via Jenkins CI job to the target host system.
- **Action:** SSH into the deployment target host and promote to user `portal`.
- **Action:** Use `docker exec -ti /bin/bash/ PORTAL_CONTAINER` to complete the container setup.
- **Action:** Setup index page in CMS as CMS Admin user.
- **Action:** Create Pre-production Portal Default Execution Systems.
- **Action:** Create Production PortalDefault Execution Systems.
- **Action:** Setup Community Data Project.
- **Action:** _Optional:_ Setup Public Data Project (if requested).
- **Action:** Run the ES Indexing management command against the deployment target host.
- **Action:** Schedule a QA Review for the deployment target host.

#### _Regular Deployment Workflow_

- **Action:** Deploy the Portal via Jenkins CI job to the target host system.
- **Action:** Schedule a QA Review for the deployment target host.

---

<a id="phase9"></a>

### _Phase 9: Maintenance_

- **Action:** TBD

---

<a id="phase10"></a>

### _Phase 10: Backups & Archiving_

- **Action:** TBD

---

<a id="phase11"></a>

### _Phase 11: Sunsetting & Retirement_

- **Action:** TBD

---

- [Index](../index.md)
