- [Index](../index.md) > [Overview](overview.md)

---

# Phase 4: Related Services & Systems

TBD...

### _Phase 4: Related Services & Systems_

- **Action:** Establish a new UT Stache entry to store project credentials and secret settings (`https://stache.utexas.edu`).
  - Each portal will require (at a minimum) the following stache entries:
    - `PORTAL_NAME v2 ADMIN Secrets` (TAPIS Tenant tokens/keys, PostgreSQL DB Cluster credentials, ElasticSearch cluster credentials, Rabbitmq credentials, Analytics, Site verification, reCAPTCHA).
    - `PORTAL_NAME v2 PPRD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
    - `PORTAL_NAME v2 PPRD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
    - `PORTAL_NAME v2 PROD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
    - `PORTAL_NAME v2 PROD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
  - _Note: The remainder of the Phase 4 steps will use the `PORTAL_NAME v2 ADMIN Secrets` UT Stache entry to document these values. They can be referenced from here later when creating the various secrets files in Phase 7._
- **Action:** Add Google Analytics property ID.
  - As the wma-portals google user, login to the Analytics dashboard.
  - Add the new property.
    - https://analytics.google.com/analytics/web/?authuser=1#/p305449396/reports/reportinghub
    - Copy the new property name and ID to the UT Stache entry for the Portal's Admin Secrets.
  - Create a new Data Stream URL for the new property.
    - Under the Analytics Portal property entry details panel, select Data Streams in the navbar, then the Add stream btn.
    - Copy the new Stream URL, Stream Name, Stream ID, Measurement ID, and the on-page tag code values into the UT Stache entry for the Portal's Admin Secrets.
    - You can also can connect the new Measurement-ID to an existing global site tag (gtag.js).
- **Action:** Generate Google Site Verification token.
  - As the wma-portal google user, login to the google search console and verify the domain DNS.
    - _Note: This requires coordination with the domain name provider to add the new google-site-verification values to the DNS configuration record for the portal vanity URL._
    - https://support.google.com/webmasters/answer/9008080#domain_name_verification&zippy=%2Cdomain-name-provider
    - https://search.google.com/u/1/search-console
- **Action:** Generate reCAPTCHA code.
  - As the wma-portals google user, login to the Google Cloud and register new keys for the vanity doamin URL.
    - https://www.google.com/u/1/recaptcha/admin/site/514551198
    - https://developers.google.com/recaptcha/intro?hl=en&authuser=1
  - Copy the keys into the UT Stache entry named `$Portal Project Name` Admin Secrets under the heading // reCAPTCHA ======/
- **Action:** Create PreProd Portal Database Credentials & Database in WMA PostgreSQL Cluster.
- **Action:** Create Production Portal Database Credentials & Database in WMA PostgreSQL Cluster.
- **Action:** Create Pre-production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.
- **Action:** Create Production Portal ElasticSearch Credentials & ES Indeces in WMA ES Cluster.
- **Action:** Create Pre-production Portal Default Storage Systems.
  - Need details on these steps.
- **Action:** Create Production Portal Default Storage Systems.

---

- [Index](../index.md) > [Overview](overview.md)
