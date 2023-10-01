# Set up haproxy, nginx, client with docker-compose, ansible

## Description

## Usage

Build and run the containers
```text
docker-compose build
docker-compose up -d
```

<br>Confirm four containers are up and running.
```
$ docker ps
CONTAINER ID   IMAGE                                     COMMAND        CREATED         STATUS        PORTS     NAMES
92d731d70f7b   setup_haproxy_nginx_ansible_b-client01    "/sbin/init"   2 seconds ago   Up 1 second   22/tcp    b-client01
747f6755d15d   setup_haproxy_nginx_ansible_b-web02       "/sbin/init"   2 seconds ago   Up 1 second   22/tcp    b-web02
f4795095f62e   setup_haproxy_nginx_ansible_b-web01       "/sbin/init"   2 seconds ago   Up 1 second   22/tcp    b-web01
bb48ff11cb42   setup_haproxy_nginx_ansible_b-haproxy01   "/sbin/init"   2 seconds ago   Up 1 second   22/tcp    b-haproxy01
```

<br>Run the playbook
```text
ansible-playbook -i inventory.ini main.yml 
```

## Smoke test

Access to the HAProxy VIP from the client
```text
ansible-playbook -i inventory.ini main.yml --tag smoke_test
```

