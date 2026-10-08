# Docker Blue-Green Deployment

Blue-Green deployment using Docker, Docker Hub and Kubernetes on a kOps cluster.

## Docker Images

- vardhan027/docker-version-demo:v1
- vardhan027/docker-version-demo:v2

## Kubernetes

Blue:
- Version: v1
- Replicas: 3
  
Green:
- Version: v2
- Replicas: 3

## Traffic Switching

Production traffic was switched from Blue to Green using:

```bash
kubectl patch service docker-demo-service -p '{"spec":{"selector":{"app":"docker-demo","version":"green"}}}'
