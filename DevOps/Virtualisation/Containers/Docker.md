---
share: true

category: Containers
---

# Docker

Docker is an open source container platform. It consists of a daemon that manages the interaction between Docker containers and the host, provisions the necessary namespaces and cgroups for each container and controls the lifecycle of each container.

## Installation


### Manual Method

(For Debian)

#### Docker CLI & Engine

**Ensure necessary dependecies are installed**:

```shell
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

Add Docker Repo GPG key:

```shell
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Add Docker Repo to a dedicated `sources.list` dropin directory:

```shell
 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Update apt cache and install Docker packages:

```shell
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```


