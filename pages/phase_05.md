# CPDP Phase 5: Deployment Target Host Provisioning

[Return to Index](../index.md)

TBD...

### _Phase 5: Deployment Target Host Provisioning_

_Note: Repeat these steps for both PPRD & PROD._

- **Task:** Generate the `dhparam.pem` file on the deployment target host.
  - `openssl genpkey -genparam -algorithm DH -out /etc/ssl/dhparam.pem -pkeyopt dh_paramgen_prime_len:4096`
- **Task:** On the deployment target host (as `root`), create the user `portal` with **no password**:
  - `sudo adduser --disabled-password portal`
- **Task:** Add the `Jenkins Deployment SSH key` to the target host's `authorized keys` file:
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
- **Task:** Nginx SSL Certs Configuration for containers:
  - When the SSL cert and key (requested in Phase 2) are placed onto the deployment host, they will be under these directories:
    - `/etc/ssl/certs/target.projectname.tacc.utexas.edu.cer.YYYYMMDD`
    - `/etc/ssl/private/target.projectname.tacc.utexas.edu.key.YYYYMMDD`
  - Create a symlink to each of these files in the same directory without the date suffix:
    - `ln -s /etc/ssl/certs/target.projectname.tacc.utexas.edu.cer.YYYYMMDD target.projectname.tacc.utexas.edu.cer`
    - `ln -s /etc/ssl/certs/target.projectname.tacc.utexas.edu.key.YYYYMMDD target.projectname.tacc.utexas.edu.key`
  - _Note: This path should match the paths mounted into the running containers in the docker `override.yml` files in `Core-Portal-Deployments`._
- **Task:** Install host dependencies:
  - `make` (for use with Camino): `sudo apt-get install make`
  - `docker` (see https://docs.docker.com/engine/install/ubuntu/)
    - See: https://docs.docker.com/engine/install/ubuntu/
  - `docker-compose`: `sudo apt-get install docker-compose containerd.io`
    - See: https://docs.docker.com/compose/install/#install-compose-on-linux-systems
- **Task:** Add the `portal` user to the (new) group `docker`: `sudo usermod -aG docker portal`
- **Task:** Create deployment directories for the Camino workflow in the PPRD deployment host.
  - `sudo mkdir /opt/portal`
  - `sudo chown portal:portal /opt/portal/`
- **Task:** Create deployment directories for the Camino workflow in the PROD deployment host.
  - Same steps as PROD.
- **Task:** Clone Camino into PPRD deployment host.
  - `sudo su - portal`
  - `cd /opt/portal`
  - `git clone https://github.com/TACC/Camino.git`
- **Task:** Clone Camino into PROD deployment host.
  - Same steps as PPRD.
- **Task:** Request SSH access for user `portal` from the Jenkins VM IP Address into the PPRD host from NSO.
- **Task:** Request SSH access for user `portal` from the Jenkins VM IP Address into the PROD host from NSO.

---

[Return to Index](../index.md)
