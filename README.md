# Kubernetes Setup for ClickHouse and Superset

This repository contains Kubernetes configurations to deploy ClickHouse and Superset, along with instructions on connecting them.

## Prerequisites

Before you begin, ensure you have the following installed and set up:

- **Minikube**: Local Kubernetes cluster for testing.
- **kubectl**: Kubernetes command-line tool.
- **Docker**: Containerization platform (if building custom images).

## Setup Instructions

### 1. Deploy ClickHouse StatefulSet

Create a StatefulSet for ClickHouse with persistent storage and expose the native port (9000).

```bash
kubectl apply -f clickhouse-statefulset.yaml
```

Deploy Superset Deployment

Create a Deployment for Superset and expose it via a NodePort service.

bash
Copy code
kubectl apply -f superset-deployment.yaml
Access Superset

Get the NodePort assigned to the Superset service:

bash
Copy code
minikube service superset --url
Open the provided URL in your browser to access Superset.

Connect ClickHouse to Superset

Log in to Superset.
Navigate to Data > Databases.
Click + Database and choose ClickHouse.
Enter the ClickHouse URL: clickhouse://default@<ClickHouse-Service-IP>:9000/default.
