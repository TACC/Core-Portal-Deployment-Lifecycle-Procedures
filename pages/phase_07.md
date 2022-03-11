- [Index](../index.md) > [Overview](overview.md)

---

# Phase 7: Secrets & CI/CD Setup

TBD...

### _Phase 7: Secrets & CI/CD Setup_

- **Reminder:** The secret values that should be contained in each stache entry:
  - `PORTAL_NAME v2 ADMIN Secrets` (TAPIS Tenant tokens/keys, PostgreSQL DB Cluster credentials, ElasticSearch cluster credentials, Rabbitmq credentials, Analytics, Site verification, reCAPTCH).
    - _Note: This entry should already be populated with these values from Phases 3 & 4._
  - `PORTAL_NAME v2 PPRD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
  - `PORTAL_NAME v2 PPRD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
  - `PORTAL_NAME v2 PROD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
  - `PORTAL_NAME v2 PROD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).

- **Action:** Populate UT Stache with the secret values specific to the PPRD CMS.
- **Action:** Populate UT Stache with the secret values specific to the PPRD Portal.
- **Action:** Populate UT Stache with the secret values specific to the PROD CMS.
- **Action:** Populate UT Stache with the secret values specific to the PROD Portal.

_Note: The SCP tasks can also be accomplished by SSHing into the target host, sudoing into user `portal`, and using vim to create and populate the files in situ._

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

- [Index](../index.md) > [Overview](overview.md)
