- [Index](../index.md) > [Overview](overview.md)

---

# Phase 7: Secrets, CI/CD Jobs & Backend Setup

## Objective

Describe the objectives of this phase of the lifecycle.

<a id="actions"></a>

### Secrets, CI/CD Jobs & Backend Systems Actions

#### [Secrets](#secrets)

- **Action:** [Populate UT Stache with the secret values specific to the PPRD CMS.](#action1)
- **Action:** [Populate UT Stache with the secret values specific to the PPRD Portal.](#action2)
- **Action:** [Populate UT Stache with the secret values specific to the PROD CMS.](#action3)
- **Action:** [Populate UT Stache with the secret values specific to the PROD Portal.](#action4)

- **Action:** [Create `secrets.py` for the PPRD django CMS container.](#action5)
- **Action:** [Create `settings_secret.py` for the PPRD django portal container.](#action6)
- **Action:** [Create `secrets.py` for the PROD django CMS container.](#action7)
- **Action:** [Create `settings_secret.py` for the PROD django portal container.](#action8)
- **Action:** [Create `rabbitmq.env` for the PPRD host.](#action9)
- **Action:** [Create `rabbitmq.env` for the PROD host.](#action10)

- **Action:** [SCP `secrets.py` into the PPRD host.](#action11)
- **Action:** [SCP `settings_secret.py` into the PPRD host.](#action12)
- **Action:** [SCP `secrets.py`  into the PROD host.](#action13)
- **Action:** [SCP `settings_secret.py` into the PROD host.](#action14)
- **Action:** [SCP `rabbitmq.env` into the PPRD host.](#action15)
- **Action:** [SCP `rabbitmq.env` into the PROD host.](#action16)

#### [CI/CD Jobs](#cicd)

- **Action:** [Configure the Portal Project Jenkins CI job.](#action17)

#### [Backend Systems](#systems)

- **Action:** [Create Pre-production Portal Default Storage Systems.](#action18)
- **Action:** [Create Production Portal Default Storage Systems.](#action19)
- **Action:** [Create PPRD Portal Default Execution Systems.](#action20)
- **Action:** [Create PROD Portal Default Execution Systems.](#action21)
- **Action:** [Setup Community Data Project.](#action22)
- **Action:** [Setup Public Data Project (if requested).](#action23)

---

<a id="instructions"></a>

## Action Instructions

<a id="secrets"></a>

### Secrets

**Reminder** - The secret values that should be contained in each stache entry:

- `PORTAL_NAME v2 ADMIN Secrets` (TAPIS Tenant tokens/keys, PostgreSQL DB Cluster credentials, ElasticSearch cluster credentials, Rabbitmq credentials, Analytics, Site verification, reCAPTCH).
  - _Note: This entry should already be populated with these values from Phases 3 & 4._
- `PORTAL_NAME v2 PPRD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
- `PORTAL_NAME v2 PPRD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).
- `PORTAL_NAME v2 PROD CMS Secrets` (Secret Key, Allowed Hosts, Auth endpoint, DB credentials, ES credentials, Haystack configuration).
- `PORTAL_NAME v2 PROD Portal Secrets` (Secret Key, DB settings, TAS settings, RT settings, Agave/TAPIS settings, RabbitMQ settings, ES settings, Celery settings, Project Keys, Custom portal configurations).

---

<a id="action1"></a>

**Action: Populate UT Stache with the secret values specific to the PPRD CMS.**

TBD...

---

<a id="action2"></a>

**Action: Populate UT Stache with the secret values specific to the PPRD Portal.**

TBD...

---

<a id="action3"></a>

**Action: Populate UT Stache with the secret values specific to the PROD CMS.**

TBD...

---

<a id="action4"></a>

**Action: Populate UT Stache with the secret values specific to the PROD Portal.**

TBD...

---

<a id="action5"></a>

**Action: Create `secrets.py` for the PPRD django CMS container.**

TBD...

---

<a id="action6"></a>

**Action: Create `settings_secret.py` for the PPRD django portal container.**

TBD...

---

<a id="action7"></a>

**Action: Create `secrets.py` for the PROD django CMS container.**

TBD...

---

<a id="action8"></a>

**Action: Create `settings_secret.py` for the PROD django portal container.**

TBD...

---

<a id="action9"></a>

**Action: Create `rabbitmq.env` for the PPRD host.**

TBD...

---

<a id="action10"></a>

**Action:** Create `rabbitmq.env` for the PROD host.

TBD...

_Note: The SCP tasks can also be accomplished by SSHing into the target host, sudoing into user `portal`, and using vim to create and populate the files in situ._

<a id="action11"></a>

**Action: SCP `secrets.py` into the PPRD host `/opt/portal/Camino/conf/cms/` subdir.**

TBD...

---

<a id="action12"></a>

**Action: SCP `settings_secret.py` into the PPRD host `/opt/portal/Camino/conf/portal/` subdir.**

TBD...

---

<a id="action13"></a>

**Action: SCP `secrets.py`  into the PROD host `/opt/portal/Camino/conf/cms/` subdir.**

TBD...

---

<a id="action14"></a>

**Action: SCP `settings_secret.py` into the PROD host `/opt/portal/Camino/conf/portal/` subdir.**

TBD...

---

<a id="action15"></a>

**Action: SCP `rabbitmq.env` into the PPRD host `/opt/portal/Camino/conf/rabbitmq/` subdir.**

TBD...

---

<a id="action16"></a>

**Action: SCP `rabbitmq.env` into the PROD host `/opt/portal/Camino/conf/rabbitmq/` subdir.**

TBD...

<a id="cicd"></a>

### CI/CD Jobs

<a id="action17"></a>

**Action: Configure the Portal Project Jenkins CI job.**

TBD...

<a id="systems"></a>

### Backend Systems

<a id="action18"></a>

**Action: Create Pre-production Portal Default Storage Systems.**

TBD...

---

<a id="action19"></a>

**Action: Create Production Portal Default Storage Systems.**

TBD...

---

<a id="action20"></a>

**Action: Create PPRD Portal Default Execution Systems.**

TBD...

---

<a id="action21"></a>

**Action: Create PROD Portal Default Execution Systems.**

TBD...

---

<a id="action22"></a>

**Action: Setup Community Data Project.**

TBD...

---

<a id="action23"></a>

**Action: Setup Public Data Project (if requested).**

TBD...

---

- [Index](../index.md) > [Overview](overview.md)
