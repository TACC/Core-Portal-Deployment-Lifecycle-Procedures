<a id="top"></a>

- [Index](../index.md) > [DevOps Lifecycle](devops.md)

---

<a id="phase-06"></a>

# Phase 6: Deployments

## Objective

Describe the objectives of this phase of the lifecycle.

<a id="actions"></a>

<a id="6a"></a>

### [6A. Administrative Prerequisites](phase_06_A#top)

- **Action:** [Identify the Portal Project PI](phase_06_A#6a-01)
- **Action:** [Identify or Establish a TAS Project/Allocation](phase_06_A#6a-02)
- **Action:** [Identify the TAS Project GID for the Portal Allocation](phase_06_A#6a-03)
- **Action:** [Ensure the Correct Users are Added to the TAS Project](phase_06_A#6a-04)
- **Action:** [Identify the WMA Developer(s) Administrating the Portal](phase_06_A#6a-05)
- **Action:** [Verify Developer Access to Required Resources](phase_06_A#6a-06)
- **Action:** [Identify the Public URL for the Portal](phase_06_A#6a-07)

<a id="6b"></a>

### [6B. Resource Planning & Allocation](phase_06_B#top)

#### Host VM Requests

- **Action:** [Request the deployment target host VMs for `PPRD`, `PROD`, `DEV`, etc. via KB.](phase_06_B#6b-01)

#### SSL Certificates

- **Action:** [Request SSL Certificates for each requested host VM via KB.](phase_06_B#6b-02)

#### WSO2 Tenant Request

- **Action:** [Select the Tenant Type for the portal (shared or dedicated).](phase_06_B#6b-03)
- **Action:** [Request a dedicated WSO2 tenant for `TAPIS` access.](phase_06_B#6b-04)
- **Action:** [Install portal service applications on the dedicated tenant.](phase_06_B#6b-05)

#### CPS Exceptions

- **Action:** [Have a CPS exception made for the `PROD` vanity domain name URL.](phase_06_B#6b-06)

<a id="6c"></a>

### [6C. Secrets & Credentials Managements](phase_06_C#top)

#### Credentials Management

- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for admin: PROJECTNAME ADMIN.](phase_06_C#6c-01)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS.](phase_06_C#6c-02)
- **Action:** [Establish new UT Stache entries to store project credentials and secret settings for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal.](phase_06_C#6c-03)

#### Tenant

- **Action:** [Create a TACC Tenant OAuth client for each host VM.](phase_06_C#6c-04)
- **Action:** [Configure TACC Tenant long lived token for each host VM.](phase_06_C#6c-05)

#### PostgreSQL

- **Action:** [Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM Portal.](phase_06_C#6c-06)
- **Action:** [Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM CMS.](phase_06_C#6c-07)

#### ElasticSearch

- **Action:** [Create ElasticSearch Credentials in the WMA ES Cluster for each host VM.](phase_06_C#6c-08)
- **Action:** [Create ElasticSearch Indeces in the WMA ES Cluster for each host VM Portal and host VM CMS.](phase_06_C#6c-09)

#### Web Services

- **Action:** [Generate a new Google Analytics property ID for the PROD vanity domain name.](phase_06_C#6c-10)
- **Action:** [Generate a new Google Site Verification token for the PROD vanity domain name.](phase_06_C#6c-11)
- **Action:** [Generate a new reCAPTCHA code for the PROD vanity domain name.](phase_06_C#6c-12)

#### Document Secrets

- **Action:** [Populate UT Stache with the secret values for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS.](phase_06_C#6c-13)
- **Action:** [Populate UT Stache with the secret values for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal.](phase_06_C#6c-14)

#### Prepare Settings

- **Action:** [Create a `secrets.py` file for the django CMS container on each host VM.](phase_06_C#6c-15)
- **Action:** [Create a `settings_secret.py` file for the django portal container on each host VM.](phase_06_C#6c-16)
- **Action:** [Create a `rabbitmq.env` file for each host VM.](phase_06_C#6c17)

<a id="6d"></a>

### [6D. Resource Provisioning & Configuration](phase_06_D#top)

#### Host Provisioning

- **Action:** [Generate the `dhparam.pem` file on the deployment target host.](phase_06_D#6d-01)
- **Action:** [On the deployment target host create the user `portal`.](phase_06_D#6d-02)
- **Action:** [Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.](phase_06_D#6d-03)
- **Action:** [Nginx SSL Certs Configuration for containers.](phase_06_D#6d-04)
- **Action:** [Install host dependencies.](phase_06_D#6d-05)
- **Action:** [Add the `portal` user to the (new) `docker` group.](phase_06_D#6d-06)
- **Action:** [Create deployment directories for the Camino workflow in each deployment host VM.](phase_06_D#6d-07)
- **Action:** [Clone Camino into each deployment host VM.](phase_06_D#6d-08)
- **Action:** [Request that NSO grant the user `portal` SSH access from the Jenkins Deployer VM IP Address into each deployment host VM.](phase_06_D#6d-09)

#### Placing Secrets

- **Action:** [SCP `secrets.py` into each deployment host VM.](phase_06_D#6d-10)
- **Action:** [SCP `settings_secret.py` into each deployment host VM.](phase_06_D#6d-11)
- **Action:** [SCP `rabbitmq.env` into each deployment host VM.](phase_06_D#6d-12)

#### CI/CD Jobs

- **Action:** [Configure the Portal Project Jenkins CI job.](phase_06_D#6d-13)

#### Backend Systems

- **Action:** [Create Default Storage Systems for the project.](phase_06_D#6d-14)
- **Action:** [Create Default Execution Systems for the project.](phase_06_D#6d-15)
- **Action:** [Setup a Community Data Project.](phase_06_D#6d-16)
- **Action:** [Setup a Public Data Project.](phase_06_D#6d-17) _(Optional)_

<a id="6e"></a>

### [6E. Branding & Image Publishing](phase_06_E#top)

- **Action:** [Setup the custom branding and navigation bar in Core-CMS-Resources.](phase_06_E#6e-01)
- **Action:** [Generate & Publish the Custom Project CMS Image on Dockerhub.](phase_06_E#6e-02)

<a id="6f"></a>

### [6F. Deployment Configurations](phase_06_F#top)

- **Action:** [Update the Core-Portal-Deployments repo with correct docker image tag values for the CMS and Portal containers.](phase_06_F#6f-01)

<a id="6g"></a>

### [6G. Deployments](phase_06_G#top)

<a id="6g1"></a>

#### [6G1. First Deployment](phase_06_G#6g1)

- **Action:** [Deploy the Portal via Jenkins CI job on the target host system.](phase_06_G#6g-01)
- **Action:** [SSH into the deployment target host and become the user `portal`.](phase_06_G#6g-02)
- **Action:** [Complete the container setup.](phase_06_G#6g-03)
- **Action:** [Create an index page in the CMS.](phase_06_G#6g-04)

<a id="6g2"></a>

#### [6G2. Regular Deployment](phase_06_G#6g2)

- **Action:** [Deploy the Portal via Jenkins CI job to each target host system.](phase_06_G#6g-05)

<a id="6h"></a>

### [6H. Post Deployment](phase_06_H#top)

- **Action:** [Run the ES Indexing management command against each deployed target host VM.](phase_06_H#6h-01)
- **Action:** [Schedule a QA Review for each deployed target host VM.](phase_06_H#6h-02)

<a class="inline-navlink-page-top" href="#top">Back to Top</a>

---

- [Index](../index.md) > [DevOps Lifecycle](devops.md)
