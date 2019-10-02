# VerneMQ Cluster

Kubernetes yaml files for deploying a VerneMQ cluster with database authentication.

## prerequisite

- create a self-signed certificate and store it to the 'certificate' folder. The repository contains a self signed certificate for demonstration purposes.

The inital database script creates the following demo login for the mqtt broker:

```
user: test-user
client: test-client
password: pass123

allowed topics: test, foo/#
```

## docker-compose

The docker compose file will create one vernemq instance and one postgres instance for local development.

'docker-compose up' will start the services.

## kubernetes

The 'apply-k8s-cluster.sh' script deploys one postgres instance and three vernemq instances to a kubernetes cluster. The script creates a separate namespace, adds the certificate to a secret and applies the kubernetes yaml files from the 'k8s' folder.

The VerneMq cluster lives behind a LoadBalancer with configured session affinity (Client Ip). 
