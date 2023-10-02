# Set up haproxy, nginx, client with docker-compose, ansible

## Description

- Launch four containers with docker-compose
- Configure a haproxy, two nginx and a client for an web access with ansible

## Usage

Install required python module.
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