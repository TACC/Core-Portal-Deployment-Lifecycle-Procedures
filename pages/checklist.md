# CEP v2 Core Portal Deployment Checklist

[Return to Index](../index.md)

## Checklist Phases

- [Phase 1: Portal Administrative Prerequisite Actions](#phase1)
- [Phase 2: Portal Resource Requests, SSH Certs & CPS Exceptions](#phase2)
- [Phase 3: Portal Tenant Setup](#phase3)
  - [Option 3A - Shared Tenant (Default)](#phase3optA)
  - [Option 3B - Dedicated Tenant](#phase3optB)
  - [Get a CPS Exception on the Tenant](#phase3cps)
- [Phase 4: Portal Related Services & Systems Setup](#phase4)
- [Phase 5: Portal Deployment Target Host Provisioning](#phase5)
- [Phase 6: Portal Branding, Content Preparation & Image Publication](#phase6)
- [Phase 7: Portal Deployment Workflow Setup](#phase7)
- [Phase 8: Portal Deployments](#phase8)
  - [Initial Deployment Workflow](#phase8IDW)
  - [Regular Deployment Workflow](#phase8RDW)
- [Phase 9: Portal Maintenance](#phase9)
- [Phase 10: Portal Backup & Archiving](#phase10)
- [Phase 11: Portal Sunsetting & Retirement](#phase11)
- [Custom Portal Development (Optional)](#custom)
- [Other Actions](#other)

---

<a id="deploymentPhases"></a>

## Portal Deployment Phases

There are several phases in the portal deployment lifecycle. Each phase is an aggregation of steps required to prepare for subsequent phases. This is the complete list of steps (referred to as a `Task`) needed to prepare, setup, configure and deploy a CEP v2 Core Portal at TACC.

_Usage_

When deploying a new portal:

- Create a JIRA `Epic` for the project (e.g. `$PORTAL_PROJECT_NAME Deployment Host Systems`).
- Create a JIRA `Task` under the new `Epic` for each _Phase_ of the portal deployment lifecycle.
- Link each _Phase_ `Task` to the project `Epic` (e.g. `is a subtask of`) in JIRA.
- Create a JIRA `Task` for each _Task_ listed under each _Phase_ of the Portal Deployment Checklist.
- Link each _Task_ `Task` to the _Phase_ `Task` (e.g. `is a subtask of`) in JIRA.
- Track the details of each _task_ `Task` in the portal deployment lifecycle using JIRA.

Detailed instructions can be found further down this page. You can quickly access them by clicking the [`link`](https://#) at the end of each task's summary description.

_TBD: Break this monolithic document into a private TACC github docs repo with pages for each Phase, with Tasks detailed there (as well as related systems architectures, etc.)._

<a id="phase1"></a>

### _Phase 1: Portal Administrative Prerequisite Actions_

- **Task:** [Identify the portal project PI.](#phase1task1)
- **Task:** [Identify the WMA developers responsible for portal setup, deployment and maintenance.](#phase1task2)
- **Task:** [Identify/establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities.](#phase1task3)
- **Task:** [Identify Portal Project TAS GID associated with the portal allocation.](#phase1task4)
- **Task:** [Ensure the correct users have admin and access to the `TAS` project.](#phase1task5)
- **Task:** [Identifyacquire the official "vanity" URL to be used by the portal.](#phase1task6)

---

<a id="phase2"></a>

### _Phase 2: Portal Resource Requests, SSH Certs & CPS Exceptions_

- **Task:** Request the deployment hosts for `PPRD` via KB.
- **Task:** Request the deployment hosts for `PROD` via KB.
- **Task:** If needed, request the deployment hosts for DEV via KB (only used in cases of custom development on a CEP fork).
- **Task:** Request SSL Certificates for the `PPRD` deployment host via KB (required to deploy the portal codebase).
- **Task:** Request SSL Certificates for the `PROD` deployment host via KB (required to deploy the portal codebase).
  - _Note: This step **cannot** be completed until the vanity URL is controlled by TACC NSO and UT EIS._
- **Task:** If used, request SSL Certificates for the `DEV` deployment host via KB (required to deploy the portal codebase).

---

<a id="phase3"></a>

### _Phase 3: Portal Tenant Setup_

<a id="phase3optA"></a>

**Option 3A - Shared Tenant** _(Default)_

- **Task:** Create a TACC Tenant OAuth client for Pre-production.
- **Task:** Create a TACC Tenant OAuth client for Production.
- **Task:** Configure TACC Tenant long lived token for Pre-production.
- **Task:** Configure TACC Tenant long lived token for Production.

<a id="phase3optB"></a>

**Option 3B - Dedicated Tenant**

- **Task:** If needed, request a dedicated `WSO2 tenant` for `TAPIS` access (requires coordination with `ACI-CIC`).
- **Task:** Complete all of the _Option A - Shared Tenant_ tasks on the custom tenant.
- **Task:** Install portal service applications on tenant (zippy, compress, extract, pems).

_After Option A or Option B..._

<a id="phase3cps"></a>

**Get a CPS Exception on the Tenant**

- **Task:** Have a CPS exception made for the `PROD` vanity domain name (only applies to conditions 1 and 2, requires coordination with `ACI-CIC`).
  - Condition 1: Using a dedicated tenant with a custom PROD domain, ensure the CPS exception is added to the tenant for the portal and its domain: `Content-Security-Policy: frame-ancestors 'self' *.tacc.utexas.edu NEWDOMAIN.COM *.NEWDOMAIN.COM;`
  - Condition 2: If using the shared tenant with a custom PROD domain, ensure the custom PROD domain is appended to the CPS frame-ancestors exceptions list for the portals-api.tacc.utexas.edu tenant: `Content-Security-Policy: frame-ancestors 'self' *.tacc.utexas.edu (...entries...) NEWDOMAIN.COM *.NEWDOMAIN.COM;`
  - Condition 3: If using the shared tenant with a standard `PORTAL.tacc.utexas.edu` domian, you do not need to take any action. The existing \*.tacc.utexas.edu value picks up all tacc subdomains automatically.

---

<a id="phase4"></a>

### _Phase 4: Portal Related Services & Systems Setup_

- **Task:** Establish a new UT Stache entry to store project credentials and secret settings (`https://stache.utexas.edu`).
  - Each portal will require (at a minimum) the following stache entries:
    - `PORTAL_NAME v2 ADMIN Secrets` (TAPIS Tenant tokens/keys, PostgreSQL DB Cluster credentials, ElasticSearch cluster credentials, Rabbitmq credentials, Analytics, Site verification, reCAPTCHA).
    - `PORTAL_NAME v2 PPRD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
    - `PORTAL_NAME v2 PPRD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
    - `PORTAL_NAME v2 PROD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
    - `PORTAL_NAME v2 PROD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
  - _Note: The remainder of the Phase 4 steps will use the `PORTAL_NAME v2 ADMIN Secrets` UT Stache entry to document these values. They can be referenced from here later when creating the various secrets files in Phase 7._
- **Task:** Add Google Analytics property ID.
  - As the wma-portals google user, login to the Analytics dashboard.
  - Add the new property.
    - https://analytics.google.com/analytics/web/?authuser=1#/p305449396/reports/reportinghub
    - Copy the new property name and ID to the UT Stache entry for the Portal's Admin Secrets.
  - Create a new Data Stream URL for the new property.
    - Under the Analytics Portal property entry details panel, select Data Streams in the navbar, then the Add stream btn.
    - Copy the new Stream URL, Stream Name, Stream ID, Measurement ID, and the on-page tag code values into the UT Stache entry for the Portal's Admin Secrets.
    - You can also can connect the new Measurement-ID to an existing global site tag (gtag.js).
- **Task:** Generate Google Site Verification token.
  - As the wma-portal google user, login to the google search console and verify the domain DNS.
    - _Note: This requires coordination with the domain name provider to add the new google-site-verification values to the DNS configuration record for the portal vanity URL._
    - https://support.google.com/webmasters/answer/9008080#domain_name_verification&zippy=%2Cdomain-name-provider
    - https://search.google.com/u/1/search-console
- **Task:** Generate reCAPTCHA code.
  - As the wma-portals google user, login to the Google Cloud and register new keys for the vanity doamin URL.
    - https://www.google.com/u/1/recaptcha/admin/site/514551198
    - https://developers.google.com/recaptcha/intro?hl=en&authuser=1
  - Copy the keys into the UT Stache entry named `$Portal Project Name` Admin Secrets under the heading // reCAPTCHA ======/
- **Task:** Create PreProd Portal Database Credentials & Database in WMA PostgreSQL Cluster.
- **Task:** Create Production Portal Database Credentials & Database in WMA PostgreSQL Cluster.
- **Task:** Create Pre-production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.
- **Task:** Create Production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.
- **Task:** Create Pre-production Portal Default Storage Systems.
  - Need details on these steps.
- **Task:** Create Production Portal Default Storage Systems.

---

<a id="phase5"></a>

### _Phase 5: Portal Deployment Target Host Provisioning_

_Note: Repeat these steps for both PPRD & PROD._

- **Task:** Generate the `dhparam.pem` file on the deployment target host.
  - `openssl genpkey -genparam -algorithm DH -out /etc/ssl/dhparam.pem -pkeyopt dh_paramgen_prime_len:4096`
- **Task:** On the deployment target host (as `root`), create the user `portal` with **no password**:
  - `sudo adduser --disabled-password portal`
- **Task:** Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file:
  - _Note: Copy the SSH key from UT Stache, another portal, or the jenkins machine itself. The cypher block should end with `jenkins@jenkins01`._
  ```
  sudo su - portal
  mkdir ~/.ssh
  vi ~/.ssh/authorized_keys
  chmod 600 .ssh/authorized_keys
  chmod 700 .ssh
  # add the SSH key (copy & paste).
  chmod 600 .ssh/authorized_keys
  ```
- **Task:** Nginx SSL Certs Configuration for containers:
  - When the SSL cert and key (requested in Phase 2) are placed onto the deployment host, they will be under these directories:
    - `/etc/ssl/certs/target.projectname.tacc.utexas.edu.cer.YYYYMMDD`
    - `/etc/ssl/private/target.projectname.tacc.utexas.edu.key.YYYYMMDD`
  - Create a symlink to each of these files in the same directory without the date suffix:
    - `ln -s /etc/ssl/certs/target.projectname.tacc.utexas.edu.cer.YYYYMMDD target.projectname.tacc.utexas.edu.cer`
    - `ln -s /etc/ssl/certs/target.projectname.tacc.utexas.edu.key.YYYYMMDD target.projectname.tacc.utexas.edu.key`
  - _Note: This path should match the paths mounted into the running containers in the docker `override.yml` files in `Core-Portal-Deployments`._
- **Task:** Install host dependencies:
  - `make` (for use with Camino): `sudo apt-get install make`
  - `docker` (see https://docs.docker.com/engine/install/ubuntu/)
    - See: https://docs.docker.com/engine/install/ubuntu/
  - `docker-compose`: `sudo apt-get install docker-compose containerd.io`
    - See: https://docs.docker.com/compose/install/#install-compose-on-linux-systems
- **Task:** Add the `portal` user to the (new) group `docker`: `sudo usermod -aG docker portal`
- **Task:** Create deployment directories for the Camino workflow in the PPRD deployment host.
  - `sudo mkdir /opt/portal`
  - `sudo chown portal:portal /opt/portal/`
- **Task:** Create deployment directories for the Camino workflow in the PROD deployment host.
  - Same steps as PROD.
- **Task:** Clone Camino into PPRD deployment host.
  - `sudo su - portal`
  - `cd /opt/portal`
  - `git clone https://github.com/TACC/Camino.git`
- **Task:** Clone Camino into PROD deployment host.
  - Same steps as PPRD.
- **Task:** Request SSH access for user `portal` from the Jenkins VM IP Address into the PPRD host from NSO.
- **Task:** Request SSH access for user `portal` from the Jenkins VM IP Address into the PROD host from NSO.

---

<a id="phase6"></a>

### _Phase 6: Portal Branding, Content Preparation & Image Publication_

- **Task:** Setup the custom branding and navigation bar in Core-CMS-Resources.
  - Use the process detailed in the `Core-CMS` (https://github.com/TACC/Core-CMS) repo `README`.
  - This phase also requires the `Core-CMS-Resources` (https://github.com/TACC/Core-CMS-Resources) repo.
- **Task:** Generate & Publish Custom CMS Image on Dockerhub.
  - In Jenkins,under the `WMA CEP` Tab, in the `Core_CMS_Build` Job, update the Choice Parameter for `CUSTOM_PROJECT` by adding the name of your deployment target to the `Choices list`.
  - **IMPORTANT:** This value must be the same value used in the `Core-CMS-Resources` repo for the project directory.
  - Once the `Core-CMS-Resources` repo is populated and the `Core_CMS_Build` job is configured, run the Jenkins job to build and publish the new CMS image:
    1. Select _Build with Parameters_.
    2. Enter the name of the `Core-CMS` repo branch to build from (if other than the default of `main`).
    3. Select the portal project from the `CUSTOM_PROJECT` dropdown list.
    4. Click the _Build_ button to Queue the job.
    5. The job icon under the **Build History** queue list (bottom-left panel of the Jenkins job view) indicates job status:
       - If the job is queuing, the icon will be grey.
       - If the job is executing, the icon will blink grey.
       - If the job is succesful, the icon will turn blue.
       - If the job fails, the icon will turn red.
  - To monitor the build job:
    1. Under the **Build History** find the new job un the queue list.
    2. Click the numbered link for the current job to open the job details view.
    3. Under the jpb details view, click the _Console Output_ link in the top-leftmenu.
    4. You can now monitor (or review) the console log output for the Jenkins job (used for troubleshooting and debugging build issues).

---

<a id="phase7"></a>

### _Phase 7: Portal Secrets & Deployment Setup_

- **Reminder:** The secret values that should be contained in each stache entry:
  - `PORTAL_NAME v2 ADMIN Secrets` (TAPIS Tenant tokens/keys, PostgreSQL DB Cluster credentials, ElasticSearch cluster credentials, Rabbitmq credentials, Analytics, Site verification, reCAPTCH).
    - _Note: This entry should already be populated with these values from Phases 3 & 4._
  - `PORTAL_NAME v2 PPRD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
  - `PORTAL_NAME v2 PPRD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
  - `PORTAL_NAME v2 PROD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
  - `PORTAL_NAME v2 PROD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).

- **Task:** Populate UT Stache with the secret values specific to the PPRD CMS.
- **Task:** Populate UT Stache with the secret values specific to the PPRD Portal.
- **Task:** Populate UT Stache with the secret values specific to the PROD CMS.
- **Task:** Populate UT Stache with the secret values specific to the PROD Portal.

_Note: The SCP tasks can also be accomplished by SSHing into the target host, sudoing into user `portal`, and using vim to create and populate the files in situ._

- **Task:** Create `secrets.py` for the PPRD django CMS container.
- **Task:** SCP `secrets.py` into the PPRD host `/opt/portal/Camino/conf/cms/` subdir.
- **Task:** Create `settings_secret.py` for the PPRD django portal container.
- **Task:** SCP `settings_secret.py` into the PPRD host `/opt/portal/Camino/conf/portal/` subdir.

- **Task:** Create `secrets.py` for the PROD django CMS container.
- **Task:** SCP `secrets.py`  into the PROD host `/opt/portal/Camino/conf/cms/` subdir.
- **Task:** Create `settings_secret.py` for the PROD django portal container.
- **Task:** SCP `settings_secret.py` into the PROD host `/opt/portal/Camino/conf/portal/` subdir.

- **Task:** Create `rabbitmq.env` (can be the same for all hosts).
- **Task:** SCP `rabbitmq.env` into the PPRD host `/opt/portal/Camino/conf/rabbitmq/` subdir.
- **Task:** SCP `rabbitmq.env` into the PROD host `/opt/portal/Camino/conf/rabbitmq/` subdir.

- **Task:** Configure Portal Project Jenkins CI job.

---

<a id="phase8"></a>

### _Phase 8: Portal Deployments_

- **Initial Deployment Workflow**: For brand new portals, complete these procedures for all deployment targets (e.g. PROD, PPRD).
- **Reqular Deployment Workflow**: Follow these procedures for existing portals.

<a id="phase8IDW"></a>

#### _Initial Deployment Workflow_

- **Task:** Deploy the Portal via Jenkins CI job to the target host system.
- **Task:** SSH into the deployment target host and promote to user `portal`.
- **Task:** Use `docker exec -ti /bin/bash/ PORTAL_CONTAINER` to complete the container setup.
  - Core Portal:
    - `docker exec -ti /bin/bash/ core_django`
    - `./manage.py migrate`
    - `./manage.py collectstatic --no-input`
    - `./manage.py createsuperuser`
      - Document admin credentials for `username:password`.
  - Core-CMS:
    - `docker exec -ti /bin/bash/ core_cms`
    - `./manage.py migrate`
    - `npm ci && npm run build`
    - `./manage.py collectstatic --no-input`
    - `./manage.py createsuperuser`
      - Document admin credentials for `username:password`.
- **Task:** Setup index page in CMS as CMS Admin user.
- **Task:** Create Pre-production Portal Default Execution Systems.
- **Task:** Create Production PortalDefault Execution Systems.
- **Task:** Setup Community Data Project.
- **Task:** _Optional:_ Setup Public Data Project (if requested).
- **Task:** Run the ES Indexing management command against the deployment target host.
- **Task:** Schedule a QA Review for the deployment target host.

<a id="phase8RDW"></a>

#### _Regular Deployment Workflow_

- **Task:** Deploy the Portal via Jenkins CI job to the target host system.
- **Task:** Schedule a QA Review for the deployment target host.

---

<a id="phase9"></a>

### _Phase 9: Portal Maintenance_

- **Task:** TBD

---

<a id="phase10"></a>

### _Phase 10: Portal Backup & Archiving_

- **Task:** TBD

---

<a id="phase11"></a>

### _Phase 11: Portal Sunsetting & Retirement_

- **Task:** TBD

---

<a id="custom"></a>

### _Custom Portal Development_ (Optional)

- **Task:** TBD

---

<a id="other"></a>

### _Other Actions_

- **Task:** TBD

---

<a id="detailed"></a>

## Detailed Task Descriptions

---

### Phase 1: Portal Administrative Prerequisite Actions

---

<a id="phase1task1"></a>

#### Task: Identify the portal project PI

Description pending.

---

<a id="phase1task2"></a>

#### Task: Identify the WMA developers responsible for portal setup, deployment and maintenance

Description pending.

---

<a id="phase1task3"></a>

#### Task: Identify/establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities

Any new portal being established must be charged against a project that is officially recognized by TACC. Additionally, any computational or storage resources used by the portal on behalf of its users must be charged against a resource allocation associated with the project. TACC users who qualify for PI status can initiate new projects in the TACC User Portal and request resource allocations.

Procedure

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

<a id="phase1task4"></a>

#### Task: Identify Portal Project TAS GID associated with the portal allocation

Description pending.

---

<a id="phase1task5"></a>

#### Task: Ensure the correct users have admin and access to the `TAS` project

Description pending.

---

<a id="phase1task6"></a>

#### Task: Identifyacquire the official "vanity" URL to be used by the portal (e.g. - `www.vanityurlfornewportal.com`)

Portal projects should request a domain name for their portal to expose for internet access by its users.

- Example. If the portal is for the Exascale Science Project, request a domain like exascale-science.org or exascalescience.org or exasci.org

Acquiring a new domain is not an immediate process. New domains first have to be purchased using funding from the project account. Once the domain has been purchased, ISO has to approve transfer of domain control over to TACC for association with the portal and the SSL certificates used to secure access to the system. Once the domain name is under TACC control, the SSL certificates required by the portal can be generated and placed into the host VMs. After the certs are in position on the host VM systems, the deployment process can proceed.

To request a new domain be acquired for a portal, submit a new ticket to the TACC consulting system under the Technology Infrastructure (TI) queue: https://consult.tacc.utexas.edu/Ticket/Create.html?Queue=1

DNS propagation status can be checked using this site: https://dnschecker.org/#CNAME/

---

[Return to Index](../index.md)

