# Day 02 – Docker & Wazuh Deployment

## Objective

Deploy the Wazuh SIEM/XDR platform using Docker Compose.

---

## Tasks Completed

- Updated Ubuntu packages
- Installed Docker Engine
- Enabled and started Docker service
- Verified Docker installation
- Ran Docker Hello World container
- Installed Docker Compose
- Learned Docker architecture
- Cloned the stable Wazuh Docker repository (v4.14.6)
- Generated TLS certificates
- Started the Wazuh platform
- Verified Manager, Indexer and Dashboard containers
- Logged into the Wazuh Dashboard

---

## Commands Used

```bash
sudo apt update
sudo apt upgrade -y

sudo apt install docker.io -y

sudo systemctl enable docker
sudo systemctl start docker

sudo docker run hello-world

docker compose version

git clone --branch v4.14.6 https://github.com/wazuh/wazuh-docker.git

cd ~/wazuh-docker/single-node

sudo docker compose -f generate-indexer-certs.yml run --rm generator

sudo docker compose up -d

sudo docker compose ps

hostname -I
```

---

## Concepts Learned

- Docker Engine
- Docker Images
- Docker Containers
- Docker Hub
- Docker Compose
- Docker Volumes
- Container Networking
- TLS Certificates
- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard

---

## Challenges Faced

- Initial repository used unavailable Docker image tags.
- Switched to the stable v4.14.6 release.
- Resolved Linux permission issue while verifying generated certificates.

---

## Result

Successfully deployed a working Wazuh SIEM/XDR platform and accessed the web dashboard.

---

## Screenshots

- 06-docker-service-running.png
- 07-docker-hello-world.png
- 09-certificates-generated.png
- 10-wazuh-containers-running.png
- 11-wazuh-dashboard-home.png