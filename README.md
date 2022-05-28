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
