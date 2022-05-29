# Docker-based testbed for CENO nodes

[![docker-compose CI](https://github.com/alekswn/inet-without-borders-2022/actions/workflows/CI.yml/badge.svg)](https://github.com/alekswn/inet-without-borders-2022/actions/workflows/CI.yml)

Docker-compose file represents:
 - CENO nodes in East and West regions isolated from each other
 - censor nodes pluged in to east and west networks both
 - Smuggler nodes (CENO nodes pluged in to both networks)
 - Jumper nodes to collect data from east region
 - Collector node

Docker build applies Ansible playbooks from https://github.com/censorship-no-archive/ceno2-testbed

Docker-compose file can be used locally or with Docker Swarm to deploy distributed network. Container images can be deployed outside of Docker Swarm manually, however they stiil will be able to reach jumper or collector node (if network topology allows it). 


### Building: 

`docker-compose build`

### Running locally:

- `docker-compose up` - runs one node of each kind dumping all logs to terminal
- `docker-compose up -d` - runs one node of each kind in background
- `docker-compose up --scale west-node=2 --scale east-node=2 -d` - runs 2 CENO nodes in east segment, 2 CENO nodes in west segment and single instance of the other services.

### Launching distributed network (NOT TESTED YET):
See [Docker Swarm docs](https://docs.docker.com/engine/swarm/)

### TODO

### Issue 1: Fix ansible playbooks for CENO node.

At the moment most of recepies are failing to apply due to outdated packages used int the recepies. Failing playbooks are commented out in [file](https://github.com/alekswn/inet-without-borders-2022/blob/main/ceno-client/ansible/localplay.yml).

### Issue 2: Check if everything setteled for CENO node.

Review [node's bootstrap document](https://github.com/censorship-no-archive/ceno2-testbed/blob/master/node.md) and factor in to ansible playbooks or Dockerfile any setup routines which were not covered by Ansible playbooks.

### Issue 3: Provision collector server

Review [server's bootstrap document](https://github.com/censorship-no-archive/ceno2-testbed/blob/master/servers.md) and implement setup for collector via Dockerfile or Ansible.

### Issue 4: Provision jumper server

Review [server's bootstrap document](https://github.com/censorship-no-archive/ceno2-testbed/blob/master/servers.md) and implement setup for jumper via Dockerfile or Ansible.

### Issue 5: Provision censor node

Implement censor based on scripts from the [archived simulator repo](https://github.com/censorship-no-archive/ceno2-simulator)

### Issue 6: Production deployment

Make it possible deployment on real network with Docker Swarm or any other way.

### Issue 7: Documentation

Document production deployment process and overall usadge.
