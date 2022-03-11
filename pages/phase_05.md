- [Index](../index.md) > [Overview](overview.md)

---

# Phase 5: Deployment Target Host Provisioning

TBD...

### _Phase 5: Deployment Target Host Provisioning_

_Note: Repeat these steps for both PPRD & PROD._

- **Action:** Generate the `dhparam.pem` file on the deployment target host.
  - `openssl genpkey -genparam -algorithm DH -out /etc/ssl/dhparam.pem -pkeyopt dh_paramgen_prime_len:4096`
- **Action:** On the deployment target host (as `root`), create the user `portal` with **no password**:
  - `sudo adduser --disabled-password portal`
- **Action:** Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file:
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
- **Action:** Nginx SSL Certs Configuration for containers:
  - When the SSL cert and key (requested in Phase 2) are placed onto the deployment host, they will be under these directories:
    - `/etc/ssl/certs/target.projectname.tacc.utexas.edu.cer.YYYYMMDD`
    - `/etc/ssl/private/target.projectname.tacc.utexas.edu.key.YYYYMMDD`
  - Create a symlink to each of these files in the same directory without the date suffix:
    - `ln -s /etc/ssl/certs/target.projectname.tacc.utexas.edu.cer.YYYYMMDD target.projectname.tacc.utexas.edu.cer`
    - `ln -s /etc/ssl/certs/target.projectname.tacc.utexas.edu.key.YYYYMMDD target.projectname.tacc.utexas.edu.key`
  - _Note: This path should match the paths mounted into the running containers in the docker `override.yml` files in `Core-Portal-Deployments`._
- **Action:** Install host dependencies:
  - `make` (for use with Camino): `sudo apt-get install make`
  - `docker` (see https://docs.docker.com/engine/install/ubuntu/)
    - See: https://docs.docker.com/engine/install/ubuntu/
  - `docker-compose`: `sudo apt-get install docker-compose containerd.io`
    - See: https://docs.docker.com/compose/install/#install-compose-on-linux-systems
- **Action:** Add the `portal` user to the (new) group `docker`: `sudo usermod -aG docker portal`
- **Action:** Create deployment directories for the Camino workflow in the PPRD deployment host.
  - `sudo mkdir /opt/portal`
  - `sudo chown portal:portal /opt/portal/`
- **Action:** Create deployment directories for the Camino workflow in the PROD deployment host.
  - Same steps as PROD.
- **Action:** Clone Camino into PPRD deployment host.
  - `sudo su - portal`
  - `cd /opt/portal`
  - `git clone https://github.com/TACC/Camino.git`
- **Action:** Clone Camino into PROD deployment host.
  - Same steps as PPRD.
- **Action:** Request SSH access for user `portal` from the Jenkins VM IP Address into the PPRD host from NSO.
- **Action:** Request SSH access for user `portal` from the Jenkins VM IP Address into the PROD host from NSO.

---

- [Index](../index.md) > [Overview](overview.md)
