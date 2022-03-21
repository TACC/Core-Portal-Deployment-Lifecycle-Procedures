- [Index](../index.md) > [Overview](overview.md)

---

<a id="phase-06"></a>

# Phase 6: Deployments

## Objective

Describe the objectives of this phase of the lifecycle.

<a id="actions"></a>

## Deployments

### 6A. Administrative Prerequisites

- **Action:** [Identify the portal project PI.](#6a-action-01)
- **Action:** [Identify or establish a `TAS` project and allocation to be used by the Portal for user access control and job submission and resource usage accounting activities.](#6a-action-02)
- **Action:** [Identify Portal Project TAS GID associated with the portal allocation.](#6a-action-03)
- **Action:** [Ensure the correct users have admin and access to the `TAS` project.](#6a-action-04)
- **Action:** [Identify the WMA developers responsible for portal setup, deployment and maintenance.](#6a-action-05)
- **Action:** [Ensure WMA developers responsible for portal setup have access to requires resources.](#6a-action-06)
- **Action:** [Identify and acquire the official "vanity" URL to be used by the portal.](#6a-action-07)

### 6B. Resource Planning & Allocation

#### Host VM Requests

- **Action:** [Request the deployment target host VMs for `PPRD`, `PROD`, `DEV`, etc. via KB.](#6b-action-01)

#### SSL Certificates

- **Action:** [Request SSL Certificates for each requested host VM via KB.](#6b-action-02)

#### WSO2 Tenant Request

- **Action:** [Select the Tenant Type for the portal (shared or dedicated).](#6b-action-03)
- **Action:** [Request a dedicated WSO2 tenant for `TAPIS` access.](#6b-action-04)
- **Action:** [Install portal service applications on the dedicated tenant.](#6b-action-05)

#### CPS Exceptions

- **Action:** [Have a CPS exception made for the `PROD` vanity domain name URL.](#6b-action-06)

### 6C. Secrets & Credentials Managements

#### Credentials Management

- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for admin: PROJECTNAME ADMIN.](#6c-action-01)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS.](#6c-action-02)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal.](#6c-action-03)

#### Tenant

- **Action:** [Create a TACC Tenant OAuth client for each host VM.](#6c-action-04)
- **Action:** [Configure TACC Tenant long lived token for each host VM.](#6c-action-05)

#### PostgreSQL

- **Action:** [Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM Portal.](#6c-action-06)
- **Action:** [Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM CMS.](#6c-action-07)

#### ElasticSearch

- **Action:** [Create ElasticSearch Credentials in the WMA ES Cluster for each host VM.](#6c-action-08)
- **Action:** [Create ElasticSearch Indeces in the WMA ES Cluster for each host VM Portal and host VM CMS.](#6c-action-09)

#### Web Services

- **Action:** [Generate a new Google Analytics property ID for the PROD vanity domain name.](#6c-action-10)
- **Action:** [Generate a new Google Site Verification token for the PROD vanity domain name.](#6c-action-11)
- **Action:** [Generate a new reCAPTCHA code for the PROD vanity domain name.](#6c-action-12)

#### Document Secrets

- **Action:** [Populate UT Stache with the secret values for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS.](#6c-action-13)
- **Action:** [Populate UT Stache with the secret values for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal.](#6c-action-14)

#### Prepare Settings

- **Action:** [Create a `secrets.py` file for the django CMS container on each host VM.](#6c-action-15)
- **Action:** [Create a `settings_secret.py` file for the django portal container on each host VM.](#6c-action-16)
- **Action:** [Create a `rabbitmq.env` file for each host VM.](#6c-action17)

### 6D. Resource Provisioning & Configuration

#### Host Provisioning

- **Action:** [Generate the `dhparam.pem` file on the deployment target host.](#6d-action-01)
- **Action:** [On the deployment target host create the user `portal`.](#6d-action-02)
- **Action:** [Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.](#6d-action-03)
- **Action:** [Nginx SSL Certs Configuration for containers.](#6d-action-04)
- **Action:** [Install host dependencies.](#6d-action-05)
- **Action:** [Add the `portal` user to the (new) `docker` group.](#6d-action-06)
- **Action:** [Create deployment directories for the Camino workflow in each deployment host VM.](#6d-action-07)
- **Action:** [Clone Camino into each deployment host VM.](#6d-action-08)
- **Action:** [Request that NSO grant the user `portal` SSH access from the Jenkins Deployer VM IP Address into each deployment host VM.](#6d-action-09)

#### Placing Secrets

- **Action:** [SCP `secrets.py` into each deployment host VM.](#6d-action-10)
- **Action:** [SCP `settings_secret.py` into each deployment host VM.](#6d-action-11)
- **Action:** [SCP `rabbitmq.env` into each deployment host VM.](#6d-action-12)

#### CI/CD Jobs

- **Action:** [Configure the Portal Project Jenkins CI job.](#6d-action-13)

#### Backend Systems

- **Action:** [Create Default Storage Systems for the project.](#6d-action-14)
- **Action:** [Create Default Execution Systems for the project.](#6d-action-15)
- **Action:** [Setup a Community Data Project.](#6d-action-16)
- **Action:** [Setup a Public Data Project.](#6d-action-17) _(Optional)_ 

### 6E. Branding & Image Publishing

- **Action:** [Setup the custom branding and navigation bar in Core-CMS-Resources.](#6e-action-01)
- **Action:** [Generate & Publish the Custom Project CMS Image on Dockerhub.](#6e-action-02)

### 6F. Deployment Configurations

- **Action:** [Update the Core-Portal-Deployments repo with correct docker image tag values for the CMS and Portal containers.](#6f-action-01)

### 6G. Deployments

#### 6G1. First Deployment

- **Action:** [Deploy the Portal via Jenkins CI job on the target host system.](#6g1-action-01)
- **Action:** [SSH into the deployment target host and become the user `portal`.](#6g1-action-02)
- **Action:** [Complete the container setup.](#6g1-action-03)
- **Action:** [Create an index page in the CMS.](#6g1-action-04)

#### 6G2. Regular Deployment

- **Action:** [Deploy the Portal via Jenkins CI job to each target host system.](#6g2-action-01)

### 6H. Post Deployment

- **Action:** [Run the ES Indexing management command against each deployed target host VM.](#6h-action-01)
- **Action:** [Schedule a QA Review for each deployed target host VM.](#6h-action-02)

---

<a id="instructions"></a>

## Action Instructions

### 6A. Administrative Prerequisites

<a id="6a-action-01"></a>

**Action: TBDI**

Description pending.

<a id="6a-action-02"></a>

**Action: TBDI**

Description pending.

<a id="6a-action-03"></a>

**Action: TBDI**

Description pending.

<a id="6a-action-04"></a>

**Action: TBDI**

Description pending.

<a id="6a-action-05"></a>

**Action: TBDI**

Description pending.

<a id="6a-action-06"></a>

**Action: TBDI**

Description pending.

<a id="6a-action-07"></a>

**Action: TBDI**

Description pending.

### 6B. Resource Planning & Allocation

TBD

### 6C. Secrets & Credentials Managements

TBD

### 6D. Resource Provisioning & Configuration

TBD

### 6E. Branding & Image Publishing

TBD

### 6F. Deployment Configurations

TBD

### 6G. Deployments

TBD

### Post Deployment

TBD

---

- [Index](../index.md) > [Overview](overview.md)
