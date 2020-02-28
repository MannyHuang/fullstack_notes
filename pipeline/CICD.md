# CICD

## workflow
- add code to branch
- merge new code to master
- travis: tigger test
- travis: build docker image
- travis: push docker image to the registry
- travis: deploy docker image to the server

## 12-Factor of DevOps
- once code base
- Explicitly declare and isolate dependencies
- Store config in the environment, not in code
- backing service should be swappable
- strictly seperate build, release and run stage
- run app as stateless process, use db for state, redis for cache
- export service via port binding
- scale out using the process model
- allows fast startup and graceful shutdown
- dev and prod should be the same
- Logs should be written to stdout app, collected by execution env
- allows to run one-time script for admin task