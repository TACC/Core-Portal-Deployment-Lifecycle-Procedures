# Core Portal Deployment Procedure: Phase 8

[Return to Index](../index.md)

## Description

TBD...

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

[Return to Index](../index.md)
