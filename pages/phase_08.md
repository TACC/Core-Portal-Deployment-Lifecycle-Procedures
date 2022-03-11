- [Index](../index.md) > [Overview](overview.md)

---

# Phase 8: Deployments

TBD...

### _Phase 8: Deployments_

- **First Deployment**: For brand new portals, complete these procedures for all deployment targets (e.g. PROD, PPRD, DEV).
- **Reqular Deployment**: Follow these procedures for existing established portals.

<a id="phase8fd"></a>

#### _First Deployment_

- **Action:** Deploy the Portal via Jenkins CI job to the target host system.
- **Action:** SSH into the deployment target host and promote to user `portal`.
- **Action:** Use `docker exec -ti /bin/bash/ PORTAL_CONTAINER` to complete the container setup.
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
- **Action:** Setup index page in CMS as CMS Admin user.

<a id="phase8systems"></a>

#### _Initiating Systems_

- **Action:** Create Pre-production Portal Default Execution Systems.
- **Action:** Create Production PortalDefault Execution Systems.
- **Action:** Setup Community Data Project.
- **Action:** _Optional:_ Setup Public Data Project (if requested).
- **Action:** Run the ES Indexing management command against the deployment target host.
- **Action:** Schedule a QA Review for the deployment target host.

<a id="phase8rd"></a>

#### _Regular Deployment_

- **Action:** Deploy the Portal via Jenkins CI job to the target host system.
- **Action:** Schedule a QA Review for the deployment target host.

---

- [Index](../index.md) > [Overview](overview.md)
