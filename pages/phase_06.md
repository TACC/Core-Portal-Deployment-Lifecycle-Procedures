- [Index](../index.md) > [Overview](overview.md)

---

# Phase 6: Branding, Content Preparation & Image Publication

TBD...

### _Phase 6: Branding, Content Preparation & Image Publication_

- **Action:** Setup the custom branding and navigation bar in Core-CMS-Resources.
  - Use the process detailed in the `Core-CMS` (https://github.com/TACC/Core-CMS) repo `README`.
  - This phase also requires the `Core-CMS-Resources` (https://github.com/TACC/Core-CMS-Resources) repo.
- **Action:** Generate & Publish Custom CMS Image on Dockerhub.
  - In Jenkins,under the `WMA CEP` Tab, in the `Core_CMS_Build` Job, update the Choice Parameter for `CUSTOM_PROJECT` by adding the name of your deployment target to the `Choices list`.
  - **IMPORTANT:** This value must be the same value used in the `Core-CMS-Resources` repo for the project directory.
  - Once the `Core-CMS-Resources` repo is populated and the `Core_CMS_Build` job is configured, run the Jenkins job to build and publish the new CMS image:
    1. Select _Build with Parameters_.
    2. Enter the name of the `Core-CMS` repo branch to build from (if other than the default of `main`).
    3. Select the portal project from the `CUSTOM_PROJECT` dropdown list.
    4. Click the _Build_ button to Queue the job.
    5. The job icon under the **Build History** queue list (bottom-left panel of the Jenkins job view) indicates job status:
       - If the job is queuing, the icon will be grey.
       - If the job is executing, the icon will blink grey.
       - If the job is succesful, the icon will turn blue.
       - If the job fails, the icon will turn red.
  - To monitor the build job:
    1. Under the **Build History** find the new job un the queue list.
    2. Click the numbered link for the current job to open the job details view.
    3. Under the jpb details view, click the _Console Output_ link in the top-leftmenu.
    4. You can now monitor (or review) the console log output for the Jenkins job (used for troubleshooting and debugging build issues).

---

- [Index](../index.md) > [Overview](overview.md)
