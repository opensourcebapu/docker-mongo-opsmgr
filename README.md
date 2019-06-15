# Docker Images for MongoDB Ops Manager

# Intro
  This repo provides dockerfiles for creating MongoDB Ops Manager Docker Images

# Version
  Latest Version: `4.0.12.50517.20190605T1533Z-1` (corresponds to version of ops manager in Dockerfile)

# Pre-Reqs
  1. Needs a MongoDB instance running at localhost:27017 on the machine you intend to run this on. Use docker-compose for easy
  local testing. Future version will add ability to change this URI. ([#2](https://github.com/opensourcebapu/docker-mongo-opsmgr/issues/2))
  2. Port 8080 open on host when using host network mode (also will change when [#2](https://github.com/opensourcebapu/docker-mongo-opsmgr/issues/2) is solved)

# Usage
  1. For manually running,a ssuming MongoDB intance is available at localhost:27017, start image with this command:
  ```bash
  docker run -d --network host opensourcebapu/mongodb-opsmgr-centos
  ```
  2. Wait approximately 2-5 minutes, then Ops Manager will be available at `http://localhost:8080`

# Credits
  1. Credits to [GradeCam](https://github.com/gradecam/docker-mongodb-ops-manager) team for entrypoint script

# References
  1. [MongoDB Ops Manager](https://www.mongodb.com/products/ops-manager)
  2. [MongoDB Ops Manager Download Page](https://www.mongodb.com/download-center/ops-manager)
