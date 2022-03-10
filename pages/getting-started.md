# CPDP: Getting Started

[Return to Index](../index.md)

## Description

This document describes steps that should be taken before beginning the deployment procedures.

### Prerequisites

In order to succesfully deploy a Core v2 Portal, you will need the following:

- Access to these service account credentials:
    - The ACI-WMA Portal Service Account
    - 

### Recommended JIRA Usage

When deploying a new portal, it can be difficult to track the individual tasks and their status, especially if the tasks are assigned to multiple team members or developers who are working in parallel. In order to facilitate the tracking of the deployment procedures, we recommend the following strategy.

**TODO: CONVERT TASK INTO SUBTASK TO BETTER DISTINGUICH FROM JIRA TASK CONCEPT.**

1. Create a JIRA `Task` under the JIRA Project for each _Phase_ of the portal deployment lifecycle.
2. Create a JIRA `Task` for each _Task_ listed under each _Phase_ in the [Deployment Procedures Checklist](pages/checklist.md)].
3. Link each _Task_ `Task` to the parent _Phase_ `Task` in JIRA (e.g. `is a subtask of`).
4. Track the progress of each _Task_ `Task` and parent _Phase_ `Task` using JIRA as usual.
