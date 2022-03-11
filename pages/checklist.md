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

### [Phase 1: Administrative Prerequisite Actions](phase_01)

- **Action:** [Identify the portal project PI.](phase_01#action1)
- **Action:** [Identify the WMA developers responsible for portal setup, deployment and maintenance.](phase_01#action2)
- **Action:** [Identify/establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities.](phase_01#action3)
- **Action:** [Identify Portal Project TAS GID associated with the portal allocation.](phase_01#action4)
- **Action:** [Ensure the correct users have admin and access to the `TAS` project.](phase_01#action5)
- **Action:** [Identifyacquire the official "vanity" URL to be used by the portal.](phase_01#action6)
- **Action:** [Ensure WMA developers responsible for portal setup have access to requires resources.](phase_01#action7)

---

<a id="phase2"></a>

### [Phase 2: Resource Requests, SSH Certs & CPS Exceptions](phase_02)

- **Action:** [Request the deployment hosts for `PPRD` via KB.](phase_02#action1)
- **Action:** [Request the deployment hosts for `PROD` via KB.](phase_02#action2)
- **Action:** [If needed, request the deployment hosts for DEV via KB.](phase_02#action3)
- **Action:** [Request SSL Certificates for the `PPRD` deployment host via KB.](phase_02#action4)
- **Action:** [Request SSL Certificates for the `PROD` deployment host via KB.](phase_02#action5)
- **Action:** [If needed, request SSL Certificates for the `DEV` deployment host via KB.](phase_02#action6)

---

<a id="phase3"></a>

### [Phase 3: OAuth Tenant](phase_03)

- **Action:** [Select Tenant Type for the portal (shared or dedicated).](phase_03#action1)

#### [Dedicated Tenant](phase_03#dedicated)

- **Action:** [Request a dedicated WSO2 tenant for `TAPIS` access.](phase_03#action2)
- **Action:** [Install portal service applications on the dedicated tenant.](phase_03#action3)

#### [Tenant Configuration](phase_03#config)

- **Action:** [Create a TACC Tenant OAuth client for Pre-production.](phase_03#action3)
- **Action:** [Create a TACC Tenant OAuth client for Production.](phase_03#action4)
- **Action:** [Configure TACC Tenant long lived token for Pre-production.](phase_03#action5)
- **Action:** [Configure TACC Tenant long lived token for Production.](phase_03#action6)

#### [CPS Exception](phase_03#cps)

- **Action:** [Have a CPS exception made for the `PROD` vanity domain name.](phase_03#action7)

---

<a id="phase4"></a>

### [Phase 4: Related Services & Systems Setup](phase_04)

- **Action:** [Establish a new UT Stache entry to store project credentials and secret settings.](phase_04#action1)
- **Action:** [Add Google Analytics property ID.](phase_04#action2)
- **Action:** [Generate Google Site Verification token.](phase_04#action3)
- **Action:** [Generate reCAPTCHA code.](phase_04#action4)
- **Action:** [Create PreProd Portal Database Credentials & Database in WMA PostgreSQL Cluster.](phase_04#action5)
- **Action:** [Create Production Portal Database Credentials & Database in WMA PostgreSQL Cluster.](phase_04#action6)
- **Action:** [Create Pre-production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.](phase_04#action7)
- **Action:** [Create Production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.](phase_04#action8)

---

<a id="phase5"></a>

### [Phase 5: Deployment Target Host Provisioning](phase_05)

_Note: Repeat these steps for both PPRD & PROD._

- **Action:** [Generate the `dhparam.pem` file on the deployment target host.](phase_05#action1)
- **Action:** [On the deployment target host create the user `portal`.](phase_05#action2)
- **Action:** [Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.](phase_05#action3)
- **Action:** [Nginx SSL Certs Configuration for containers.](phase_05#action4)
- **Action:** [Install host dependencies.](phase_05#action5)
- **Action:** [Add the `portal` user to the (new) `docker` group.](phase_05#action6)
- **Action:** [Create deployment directories for the Camino workflow in the PPRD deployment host.](phase_05#action7)
- **Action:** [Create deployment directories for the Camino workflow in the PROD deployment host.](phase_05#action8)
- **Action:** [Clone Camino into PPRD deployment host.](phase_05#action9)
- **Action:** [Clone Camino into PROD deployment host.](phase_05#action10)
- **Action:** [Request SSH access for user `portal` from the Jenkins VM IP Address into the PPRD host from NSO.](phase_05#action11)
- **Action:** [Request SSH access for user `portal` from the Jenkins VM IP Address into the PROD host from NSO.](phase_05#action12)

---

<a id="phase6"></a>

### [Phase 6: Branding, Content Preparation & Image Publication](phase_06)

- **Action:** [Setup the custom branding and navigation bar in Core-CMS-Resources.](phase_06#action1)
- **Action:** [Generate & Publish Custom CMS Image on Dockerhub.](phase_06#action2)

---

<a id="phase7"></a>

### [Phase 7: Secrets, CI/CD Jobs & Backend Systems](phase_07)

#### [Secrets](phase_07#secrets)

- **Action:** [Populate UT Stache with the secret values specific to the PPRD CMS.](phase_07#action1)
- **Action:** [Populate UT Stache with the secret values specific to the PPRD Portal.](phase_07#action2)
- **Action:** [Populate UT Stache with the secret values specific to the PROD CMS.](phase_07#action3)
- **Action:** [Populate UT Stache with the secret values specific to the PROD Portal.](phase_07#action4)

- **Action:** [Create `secrets.py` for the PPRD django CMS container.](phase_07#action5)
- **Action:** [Create `settings_secret.py` for the PPRD django portal container.](phase_07#action6)
- **Action:** [Create `secrets.py` for the PROD django CMS container.](phase_07#action7)
- **Action:** [Create `settings_secret.py` for the PROD django portal container.](phase_07#action8)
- **Action:** [Create `rabbitmq.env` for the PPRD host.](phase_07#action9)
- **Action:** [Create `rabbitmq.env` for the PROD host.](phase_07#action10)

- **Action:** [SCP `secrets.py` into the PPRD host.](phase_07#action11)
- **Action:** [SCP `settings_secret.py` into the PPRD host.](phase_07#action12)
- **Action:** [SCP `secrets.py`  into the PROD host.](phase_07#action13)
- **Action:** [SCP `settings_secret.py` into the PROD host.](phase_07#action14)
- **Action:** [SCP `rabbitmq.env` into the PPRD host.](phase_07#action15)
- **Action:** [SCP `rabbitmq.env` into the PROD host.](phase_07#action16)

#### [CI/CD Jobs](phase_07#cicd)

- **Action:** [Configure the Portal Project Jenkins CI job.](phase_07#action17)

#### [Backend Systems](phase_07#systems)

- **Action:** [Create Pre-production Portal Default Storage Systems.](phase_07#action18)
- **Action:** [Create Production Portal Default Storage Systems.](phase_07#action19)
- **Action:** [Create PPRD Portal Default Execution Systems.](phase_07#action20)
- **Action:** [Create PROD Portal Default Execution Systems.](phase_07#action21)
- **Action:** [Setup Community Data Project.](phase_07#action22)
- **Action:** [Setup Public Data Project (if requested).](phase_07#action23)

---

<a id="phase8"></a>

### [Phase 8: Deployments](phase_08)

- **First Deployment**: [New portals.](phase8#fd)
- **Reqular Deployment**: [Established portals.](phase8#rd)

<a id="phase8fd"></a>

#### [First Deployment](phase_08#fd)

- **Action:** [Deploy the Portal via Jenkins CI job on the target host system.](phase_08#action1)
- **Action:** [SSH into the deployment target host and promote to user `portal`.](phase_08#action2)
- **Action:** [Complete the container setup.](phase_08#action3)
- **Action:** [Create index page in CMS.](phase_08#action4)

<a id="phase8rd"></a>

#### [Regular Deployment](phase_08#rd)

- **Action:** [Deploy the Portal via Jenkins CI job to the target host system.](phase_08#action5)
- **Action:** [Schedule a QA Review for the deployment target host.](phase_08#action6)

<a id="phase8pda"></a>

#### [Post Deployment Actions](phase_08#pda)

- **Action:** [Run the ES Indexing management command against the deployment target host.](phase_08#action7)
- **Action:** [Schedule a QA Review for the deployment target host.](phase_08#action8)

---

<a id="phase9"></a>

### [Phase 9: Maintenance](phase_09)

- **Action:** [TBD](phase_09#action1)

---

<a id="phase10"></a>

### [Phase 10: Backups & Archiving](phase_10)

- **Action:** [TBD](phase_10#action1)

---

<a id="phase11"></a>

### [Phase 11: Sunsetting & Retirement](phase_11)

- **Action:** [TBD](phase_11#action1)

---

- [Index](../index.md)
