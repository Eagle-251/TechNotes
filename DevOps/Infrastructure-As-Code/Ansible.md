---
share: true

category: Infrastructure As Code
telegraph_page_url: https://telegra.ph/Ansible-06-01-2
telegraph_page_path: Ansible-06-01-2
---

# Ansible

## Installation

### Fedora

`sudo dnf install ansible`

### Ubuntu

```shell
sudo apt update 
sudo apt install software-properties-common 
sudo add-apt-repository --yes --update ppa:ansible/ansible 
sudo apt install ansible
```


## Configuration

## Modules
### Docker
Ansible has _many_ modules for Docker. Ranging from managing Containers, setting up Docker Swarm stacks to using docker compose.

#### Docker Container 
_manage docker containers_

##### Examples
- Networks
```yaml
- name: Start container, connect to network and link
  community.docker.docker_container:
    name: sleeper
    image: ubuntu:14.04
    networks:
      - name: TestingNet
        ipv4_address: "172.16.1.100"
        aliases:
          - sleepyzz
        links:
          - db_test:db
      - name: TestingNet2
```
- Create Multiple containers with looping
```yaml
- name: Start 4 load-balanced containers
  community.docker.docker_container:
    name: "container{{ item }}"
	 recreate: yes
	 image: someuser/anotherappimage
	 command: sleep 1d
  with_sequence: count=4  
```



## Cheatsheet
### Playbook Running

### Vault Operations



