

##### Docker Desktop
[Source](https://docs.docker.com/desktop/setup/install/linux/ubuntu/)
1. Run
```bash
 sudo apt-get install ./docker-desktop-amd64.deb
```
2. [Download DEP package](https://desktop.docker.com/linux/main/amd64/docker-desktop-amd64.deb?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64)

##### Docker & Docker Compose
[Source](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
```bash
sudo apt-get update
sudo apt-get install ca-certificates curl

sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker $USER
newgrp docker
sudo systemctl status docker
```
⚠️ **Log out and back in** so `docker` command works without `sudo`.

##### Is installed?
```bash
docker --version
docker compose version
```
##### Test
```bash
docker run hello-world
```