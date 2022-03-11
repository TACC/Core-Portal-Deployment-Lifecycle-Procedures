- [Index](../index.md) > [Overview](overview.md)

---

# CPLDP Phase 3: OAuth Tenants

TBD...

### _Phase 3: OAuth Tenants_

<a id="phase3optA"></a>

**Option 3A - Shared Tenant** _(Default)_

- **Action:** Create a TACC Tenant OAuth client for Pre-production.
- **Action:** Create a TACC Tenant OAuth client for Production.
- **Action:** Configure TACC Tenant long lived token for Pre-production.
- **Action:** Configure TACC Tenant long lived token for Production.

<a id="phase3optB"></a>

**Option 3B - Dedicated Tenant**

- **Action:** If needed, request a dedicated `WSO2 tenant` for `TAPIS` access (requires coordination with `ACI-CIC`).
- **Action:** Complete all of the _Option A - Shared Tenant_ tasks on the custom tenant.
- **Action:** Install portal service applications on tenant (zippy, compress, extract, pems).

_After Option A or Option B..._

<a id="phase3cps"></a>

**Get a CPS Exception on the Tenant**

- **Action:** Have a CPS exception made for the `PROD` vanity domain name (only applies to conditions 1 and 2, requires coordination with `ACI-CIC`).
  - Condition 1: Using a dedicated tenant with a custom PROD domain, ensure the CPS exception is added to the tenant for the portal and its domain: `Content-Security-Policy: frame-ancestors 'self' *.tacc.utexas.edu NEWDOMAIN.COM *.NEWDOMAIN.COM;`
  - Condition 2: If using the shared tenant with a custom PROD domain, ensure the custom PROD domain is appended to the CPS frame-ancestors exceptions list for the portals-api.tacc.utexas.edu tenant: `Content-Security-Policy: frame-ancestors 'self' *.tacc.utexas.edu (...entries...) NEWDOMAIN.COM *.NEWDOMAIN.COM;`
  - Condition 3: If using the shared tenant with a standard `PORTAL.tacc.utexas.edu` domian, you do not need to take any action. The existing \*.tacc.utexas.edu value picks up all tacc subdomains automatically.

---

- [Index](../index.md) > [Overview](overview.md)
