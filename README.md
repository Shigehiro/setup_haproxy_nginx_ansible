# Set up haproxy, nginx, client with docker-compose, ansible

## Description

## Usage

Build and run the containers
```text
docker-compose build
docker-compose up -d
```

<br>Run the playbook
```text
ansible-playbook -i inventory.ini main.yml 
```