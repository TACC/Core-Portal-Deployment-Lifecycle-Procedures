- [Index](../index.md) > [Overview](overview.md)

---

<a id="phase5"></a>

# Phase 5: Deployment Target Host Provisioning

## Objective

Describe the objectives of this phase of the lifecycle.

## Deployment Target Host Provisioning Actions

_Note: Repeat these steps for each deployment target host._

- **Action:** [Generate the `dhparam.pem` file on the deployment target host.](#action1)
- **Action:** [On the deployment target host create the user `portal`.](#action2)
- **Action:** [Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.](#action3)
- **Action:** [Nginx SSL Certs Configuration for containers.](#action4)
- **Action:** [Install host dependencies.](#action5)
- **Action:** [Add the `portal` user to the (new) `docker` group.](#action6)
- **Action:** [Create deployment directories for the Camino workflow in the PPRD deployment host.](#action7)
- **Action:** [Create deployment directories for the Camino workflow in the PROD deployment host.](#action8)
- **Action:** [Clone Camino into PPRD deployment host.](#action9)
- **Action:** [Clone Camino into PROD deployment host.](#action10)
- **Action:** [Request SSH access for user `portal` from the Jenkins VM IP Address into the PPRD host from NSO.](#action11)
- **Action:** [Request SSH access for user `portal` from the Jenkins VM IP Address into the PROD host from NSO.](#action12)

---

<a id="instructions"></a>

## Action Instructions

<a id="action1"></a>

**Action: Generate the `dhparam.pem` file on the deployment target host.**

  - `openssl genpkey -genparam -algorithm DH -out /etc/ssl/dhparam.pem -pkeyopt dh_paramgen_prime_len:4096`

---

<a id="action2"></a>

**Action: On the deployment target host (as `root`), create the user `portal`.**

  - Create user with **no password**
  - `sudo adduser --disabled-password portal`

---

<a id="action3"></a>

**Action: Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file.**

  - _Note: Copy the SSH key from UT Stache, another portal, or the jenkins machine itself. The cypher block should end with `jenkins@jenkins01`._
  ```
  sudo su - portal
  mkdir ~/.ssh
  vi ~/.ssh/authorized_keys
  chmod 600 .ssh/authorized_keys
  chmod 700 .ssh
  # add the SSH key (copy & paste).
  chmod 600 .ssh/authorized_keys
  ```

---

<a id="action4"></a>

**Action: Nginx SSL Certs Configuration for containers.**

  - When the SSL cert and key (requested in Phase 2) are placed onto the deployment host, they will be under these directories:
    - `/etc/ssl/certs/target.projectname.tacc.utexas.edu.cer.YYYYMMDD`
    - `/etc/ssl/private/target.projectname.tacc.utexas.edu.key.YYYYMMDD`
  - Create a symlink to each of these files in the same directory without the date suffix:
    - `ln -s /etc/ssl/certs/target.projectname.tacc.utexas.edu.cer.YYYYMMDD target.projectname.tacc.utexas.edu.cer`
    - `ln -s /etc/ssl/certs/target.projectname.tacc.utexas.edu.key.YYYYMMDD target.projectname.tacc.utexas.edu.key`
  - _Note: This path should match the paths mounted into the running containers in the docker `override.yml` files in `Core-Portal-Deployments`._


---

<a id="action5"></a>

**Action: Install host dependencies.**

  - `make` (for use with Camino): `sudo apt-get install make`
  - `docker` (see https://docs.docker.com/engine/install/ubuntu/)
    - See: https://docs.docker.com/engine/install/ubuntu/
  - `docker-compose`: `sudo apt-get install docker-compose containerd.io`
    - See: https://docs.docker.com/compose/install/#install-compose-on-linux-systems

---

<a id="action6"></a>

**Action: Add the `portal` user to the (new) group `docker`: `sudo usermod -aG docker portal`**

TBD.

---

<a id="action7"></a>

**Action: Create deployment directories for the Camino workflow in the PPRD deployment host.**

  - `sudo mkdir /opt/portal`
  - `sudo chown portal:portal /opt/portal/`

---

<a id="action8"></a>

**Action: Create deployment directories for the Camino workflow in the PROD deployment host.**

  - Same steps as PROD.

---

<a id="action9"></a>

**Action: Clone Camino into PPRD deployment host.**

  - `sudo su - portal`
  - `cd /opt/portal`
  - `git clone https://github.com/TACC/Camino.git`

---

<a id="action10"></a>

**Action: Clone Camino into PROD deployment host.**

  - Same steps as PPRD.

---

<a id="action11"></a>

**Action: Request SSH access for user `portal` from the Jenkins VM IP Address into the PPRD host from NSO.**

TBD.

---

<a id="action12"></a>

**Action: Request SSH access for user `portal` from the Jenkins VM IP Address into the PROD host from NSO.**

TBD.

---

- [Index](../index.md) > [Overview](overview.md)
