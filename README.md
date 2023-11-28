# Set up haproxy, nginx, client with docker-compose, ansible

## Description

- Launch four init containers with docker-compose
- Configure a haproxy, two nginx and a client for an web access with ansible

[![asciicast](https://asciinema.org/a/cXfM7CwFWokrmDk0X8NTm7wdi.png)](https://asciinema.org/a/cXfM7CwFWokrmDk0X8NTm7wdi)

## Tested Environment

```text
# cat /etc/fedora-release 
Fedora release 39 (Thirty Nine)

# docker info |grep -E 'Server Version|Cgroup Version'
 Server Version: 24.0.7
 Cgroup Version: 2

# docker compose version
Docker Compose version v2.21.0
```

## Prerequisite

- Install Docker Engine and Docker Compose
- This playbook is not tested with Podman or Podman-Compose
- Confirmed this worked on Fedora 39, CentOS Stream 9, and Rocky 9

## Usage

Install required Python module.
```text
cd setup_haproxy_nginx_ansible/
```

```text
python3 -m venv venv
```

```text
source venv/bin/activate
```

```text
pip install pip --upgrade
```

```text
pip install -r requirements.txt
```

<br>Build containers.
```text
docker-compose build
```

<br>Run the containers.
```text
docker-compose up -d
```

<br>Confirm four containers are up and running.
```text
docker ps
```

<br>Run the playbook
```text
ansible-playbook -i inventory.ini main.yml 
```

<br>**Smoke test**<br>
Access to the HAProxy VIP from the client
```text
ansible-playbook -i inventory.ini main.yml --tag smoke_test
```

## Ansible vars

See group_vars.
```text
ls group_vars/
```