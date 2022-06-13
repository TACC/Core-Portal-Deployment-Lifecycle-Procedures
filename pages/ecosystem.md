- [Index](../index.md)

---

# Core Portal Ecosystem

The TACC Core Experience Portal (CEP) provides an “out-of-the -box” solution for rapidly deploying a new portal project with all the common capabilities of the base portal. CEP is used in TACC portal projects and multiple content-only (aka Stand Alone Deployment or SAD CMS) sites. CEP is comprised of multiple codebases that interoperate on a shared deployment target host.

## Portal Objectives

Establishing a common codebase for all TACC portals helps maintain alignment between the core capabilities and technologies we support across all TACC portals and in the larger context of the data center ecosystem. CEP provides new portal projects with all the common base capabilities in place, compliant with current best practices and conventions at TACC.

### Common Portal Capabilities

- Dedicated VM resources for each portal (varies by portal requirements).
- An isolated tenant for integration into the TACC ecosystem via the portal.
- A CMS for adding/editing content within static portal pages.
- Integrated Elastic Search.
- An Issue Tracking & Ticketing System (integrated with the TACC RT ticketing system).
- User account authentication (requires a TACC account).
- A user-based Dashboard to monitor project activity and resource utilization.
- A shared Community Data storage system for collaborative data.
- A Private Data storage system for individual data.
- Execution Systems for running applications.
- An Application Launcher for accessing public and private applications.
- A shared My Projects storage system for non-public group projects.
- A Public Data storage area for unauthenticated access to published work or data sets.

### CEP Major Components

- General Content Management System (user content creation)
- My Account (user account management)
- My Dashboard (user & systems information)
- Data Depot (data files & storage systems)
- Workspace (aplpications & execution systems)
- Search (user generated files & portal content)
- Notifications (system messages to the user)

### Portal Customization

There will be unique requirements for some portal projects. Any additional portal capabilities required by a project need to be identified and planned for independently. If new or enhanced features are developed for a CEP-based portal, they will be shared across all portal projects based on CEP. Likewise, if a new capability is developed for a CEP-based project using custom containers, TAPIS applications, or in extreme cases - a forked version of the CEP codebase, that capability can be pushed back upstream to the Core ecosystem to be shared by any sibling projects that wish to utilize the new capability.

---

- [Index](../index.md)
