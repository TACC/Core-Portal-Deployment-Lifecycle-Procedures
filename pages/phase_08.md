- [Index](../index.md) > [Overview](overview.md)

---

# Phase 8: Deployments

## Objective

Describe the objectives of this phase of the lifecycle.

<a id="actions"></a>

### Deployments Actions

#### [Deployments](#deployments)

- **First Deployment**: [New portals.](#fd)
- **Reqular Deployment**: [Established portals.](#rd)

<a id="fd"></a>

#### [First Deployment](#fdi)

- **Action:** [Deploy the Portal via Jenkins CI job on the target host system.](#action1)
- **Action:** [SSH into the deployment target host and promote to user `portal`.](#action2)
- **Action:** [Complete the container setup.](#action3)
- **Action:** [Create index page in CMS.](#action4)

<a id="rd"></a>

#### [Regular Deployment](#rdi)

- **Action:** [Deploy the Portal via Jenkins CI job to the target host system.](#action5)
- **Action:** [Schedule a QA Review for the deployment target host.](#action6)

<a id="pda"></a>

#### [Post Deployment Actions](#pda)

- **Action:** [Run the ES Indexing management command against the deployment target host.](#action7)
- **Action:** [Schedule a QA Review for the deployment target host.](#action8)

---

<a id="instructions"></a>

## Action Instructions

<a id="deployments"></a>

### Deployments

- **First Deployment**: For brand new portals, complete these procedures for all deployment targets (e.g. PROD, PPRD, DEV).
- **Reqular Deployment**: Follow these procedures for existing established portals.

<a id="fdi"></a>

#### First Deployment

<a id="action1"></a>

**Action: Deploy the Portal via Jenkins CI job to the target host system.**

TBD...

<a id="action2"></a>

**Action: SSH into the deployment target host and promote to user `portal`.**

TBD...

<a id="action3"></a>

**Action: Use `docker exec -ti /bin/bash/ PORTAL_CONTAINER` to complete the container setup.**

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

<a id="action4"></a>

**Action: Setup index page in CMS as CMS Admin user.**

<a id="rdi"></a>

#### Regular Deployment

<a id="action5"></a>

**Action:** Deploy the Portal via Jenkins CI job to the target host system.

TBD...

<a id="action6"></a>

**Action:** Schedule a QA Review for the deployment target host.

TBD...

<a id="pda"></a>

#### Post Deployment Actions

<a id="action7"></a>

**Action:** Run the ES Indexing management command against the deployment target host.

TBD...

<a id="action8"></a>

**Action:** Schedule a QA Review for the deployment target host.

TBD...

---

- [Index](../index.md) > [Overview](overview.md)
