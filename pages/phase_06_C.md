<a id="top"></a>

- [Index](../index.md) > [DevOps Lifecycle](devops.md) > [Phase 6](phase_06.md)

---

<a id="actions"></a>

# Phase 6C: Secrets & Credentials Managements

## Credentials Management

<a id="6c-01"></a>

### Establish new UT Stache entry to store Administrator credentials

Create a new entry for the admin credentials and secret settings.
Name the new entry `PROJECTNAME Administrator`.

<a id="6c-02"></a>

### Establish new UT Stache entries to store Portal credentials

Create new entries for the Portal credentials and secret settings.
Name the new entries for each deployment target host system:

- `PROJECTNAME PROD Portal`
- `PROJECTNAME PPRD Portal`

<a id="6c-03"></a>

### Establish new UT Stache entries to store CMS credentials

Create new entries for the CMS credentials and secret settings.
Name the new entries for each deployment target host system:

- `PROJECTNAME PROD CMS`
- `PROJECTNAME PPRD CMS`

## WSO2 Tenant

<a id="6c-04"></a>

### Create a TACC Tenant OAuth client for each host VM

Description pending.

<a id="6c-05"></a>

### Configure TACC Tenant long lived token for each host VM

Description pending.

## PostgreSQL

<a id="6c-06"></a>

### Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM Portal

Description pending.

<a id="6c-07"></a>

### Create Database Credentials & a Database in the WMA PostgreSQL Cluster for each host VM CMS

Description pending.

## ElasticSearch

<a id="6c-08"></a>

### Create ElasticSearch Credentials in the WMA ES Cluster for each host VM

Description pending.

<a id="6c-09"></a>

### Create ElasticSearch Indeces in the WMA ES Cluster for each host VM Portal and host VM CMS

Description pending.

## Web Services

<a id="6c-10"></a>

### Generate a new Google Analytics property ID for the PROD vanity domain name

Description pending.

<a id="6c-11"></a>

### Generate a new Google Site Verification token for the PROD vanity domain name

Description pending.

<a id="6c-12"></a>

### Generate a new reCAPTCHA code for the PROD vanity domain name

Description pending.

## Document Secrets

<a id="6c-13"></a>

### Populate UT Stache with the secret values for each host VM CMS: PROJECTNAME DEPLOYMENT_TARGET CMS

Description pending.

<a id="6c-14"></a>

### Populate UT Stache with the secret values for each host VM Portal: PROJECTNAME DEPLOYMENT_TARGET Portal

Description pending.

## Prepare Settings

<a id="6c-15"></a>

### Create a `secrets.py` file for the django CMS container on each host VM

Description pending.

<a id="6c-16"></a>

### Create a `settings_secret.py` file for the django portal container on each host VM

Description pending.

<a id="6c-17"></a>

### Create a `rabbitmq.env` file for each host VM

Description pending.

<a class="inline-navlink-page-top" href="#actions">Back to Top</a>

---

- [Index](../index.md) > [DevOps Lifecycle](devops.md) > [Phase 6](phase_06.md)
