- [Index](../index.md) > [Overview](overview.md)

---

# Phase 3: OAuth Tenant

## Objective

Describe the objectives of this phase of the lifecycle.

<a id="actions"></a>

### OAuth Tenant Actions

- **Action:** [Select Tenant Type for the portal (shared or dedicated).](#action1)
  - [Shared Tenant](#shared)
  - [Dedicated Tenant](#dedicated)
- **Action:** [Request a dedicated WSO2 tenant for `TAPIS` access.](#action2)
- **Action:** [Install portal service applications on the dedicated tenant.](#action3)

#### [Tenant Configuration](#configure)

- **Action:** [Create a TACC Tenant OAuth client for Pre-production.](#action3)
- **Action:** [Create a TACC Tenant OAuth client for Production.](#action4)
- **Action:** [Configure TACC Tenant long lived token for Pre-production.](#action5)
- **Action:** [Configure TACC Tenant long lived token for Production.](#action6)

#### [CPS Exception](#cps)

- **Action:** [Have a CPS exception made for the `PROD` vanity domain name.](#action7)

---

<a id="instructions"></a>

## Action Instructions

<a id="action1"></a>

**Action: Select Tenant type for the portal (shared or dedicated).** 

- Dedicated tenants require additional actions.

<a id="shared"></a>

### Option 3A - Shared Tenant _(Default)_

This tenant exists already. No further action is required to establish a tenant for the portal.

<a id="dedicated"></a>

### Option 3B - Dedicated Tenant

<a id="action2"></a>

**Action: If needed, request a dedicated WSO2 tenant for `TAPIS` access (requires coordination with `ACI-CIC`).**

TBD...

---

<a id="action3"></a>

**Action: Install portal service applications on tenant (zippy, compress, extract, pems).**

TBD...

---

_After Option A or Option B..._

<a id="configure"></a>

### Configure Tenant Clients

<a id="action4"></a>

**Action: Create a TACC Tenant OAuth client for Pre-production.**

TBD...

---

<a id="action5"></a>

**Action: Create a TACC Tenant OAuth client for Production.**

TBD...

---

<a id="action6"></a>

**Action: Configure TACC Tenant long lived token for Pre-production.**

TBD...

---

<a id="action7"></a>

**Action: Configure TACC Tenant long lived token for Production.**

TBD...

---

<a id="cps"></a>

### Get a CPS Exception on the Tenant**

<a id="action8"></a>

**Action: Have a CPS exception made for the `PROD` vanity domain name.**

- _Note: This only applies to conditions 1 and 2, requires coordination with `ACI-CIC`_.

Condition 1: Using a dedicated tenant with a custom PROD domain, ensure the CPS exception is added to the tenant for the portal and its domain: `Content-Security-Policy: frame-ancestors 'self' *.tacc.utexas.edu NEWDOMAIN.COM *.NEWDOMAIN.COM;`

Condition 2: If using the shared tenant with a custom PROD domain, ensure the custom PROD domain is appended to the CPS frame-ancestors exceptions list for the portals-api.tacc.utexas.edu tenant: `Content-Security-Policy: frame-ancestors 'self' *.tacc.utexas.edu (...entries...) NEWDOMAIN.COM *.NEWDOMAIN.COM;`

Condition 3: If using the shared tenant with a standard `PORTAL.tacc.utexas.edu` domian, you do not need to take any action. The existing \*.tacc.utexas.edu value picks up all tacc subdomains automatically.

---

- [Index](../index.md) > [Overview](overview.md)
