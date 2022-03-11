- [Index](../index.md) > [Overview](overview.md)

---

<a id="phase4"></a>

# Phase 4: Related Services & Systems

## Objective

Describe the objectives of this phase of the lifecycle.

## Related Services & Systems Actions

- **Action:** [Establish a new UT Stache entry to store project credentials and secret settings.](#action1)
- **Action:** [Add Google Analytics property ID.](#action2)
- **Action:** [Generate Google Site Verification token.](#action3)
- **Action:** [Generate reCAPTCHA code.](#action4)
- **Action:** [Create PreProd Portal Database Credentials & Database in WMA PostgreSQL Cluster.](#action5)
- **Action:** [Create Production Portal Database Credentials & Database in WMA PostgreSQL Cluster.](#action6)
- **Action:** [Create Pre-production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.](#action7)
- **Action:** [Create Production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.](#action8)

---

<a id="instructions"></a>

## Action Instructions

<a id="action1"></a>

**Action: Establish a new UT Stache entry to store project credentials and secret settings (`https://stache.utexas.edu`).**

  - Each portal will require (at a minimum) the following stache entries:
    - `PORTAL_NAME v2 ADMIN Secrets` (TAPIS Tenant tokens/keys, PostgreSQL DB Cluster credentials, ElasticSearch cluster credentials, Rabbitmq credentials, Analytics, Site verification, reCAPTCHA).
    - `PORTAL_NAME v2 PPRD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
    - `PORTAL_NAME v2 PPRD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
    - `PORTAL_NAME v2 PROD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
    - `PORTAL_NAME v2 PROD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
  - _Note: The remainder of the Phase 4 steps will use the `PORTAL_NAME v2 ADMIN Secrets` UT Stache entry to document these values. They can be referenced from here later when creating the various secrets files in Phase 7._

---

<a id="action2"></a>

**Action: Add Google Analytics property ID.**

  - As the wma-portals google user, login to the Analytics dashboard.
  - Add the new property.
    - https://analytics.google.com/analytics/web/?authuser=1#/p305449396/reports/reportinghub
    - Copy the new property name and ID to the UT Stache entry for the Portal's Admin Secrets.
  - Create a new Data Stream URL for the new property.
    - Under the Analytics Portal property entry details panel, select Data Streams in the navbar, then the Add stream btn.
    - Copy the new Stream URL, Stream Name, Stream ID, Measurement ID, and the on-page tag code values into the UT Stache entry for the Portal's Admin Secrets.
    - You can also can connect the new Measurement-ID to an existing global site tag (gtag.js).

---

<a id="action3"></a>

**Action: Generate Google Site Verification token.**

  - As the wma-portal google user, login to the google search console and verify the domain DNS.
    - _Note: This requires coordination with the domain name provider to add the new google-site-verification values to the DNS configuration record for the portal vanity URL._
    - https://support.google.com/webmasters/answer/9008080#domain_name_verification&zippy=%2Cdomain-name-provider
    - https://search.google.com/u/1/search-console

---

<a id="action4"></a>

**Action: Generate reCAPTCHA code.**

  - As the wma-portals google user, login to the Google Cloud and register new keys for the vanity doamin URL.
    - https://www.google.com/u/1/recaptcha/admin/site/514551198
    - https://developers.google.com/recaptcha/intro?hl=en&authuser=1
  - Copy the keys into the UT Stache entry named `$Portal Project Name` Admin Secrets under the heading // reCAPTCHA ======/

---

<a id="action5"></a>

**Action: Create PreProd Portal Database Credentials & Database in WMA PostgreSQL Cluster.**

TBD.

---

<a id="action6"></a>

**Action: Create Production Portal Database Credentials & Database in WMA PostgreSQL Cluster.**

TBD.

---

<a id="action7"></a>

**Action: Create Pre-production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.**

TBD.

---

<a id="action8"></a>

**Action: Create Production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.**

TBD.

---

- [Index](../index.md) > [Overview](overview.md)
