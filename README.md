# Docker Blue-Green Deployment

## Architecture

GitHub → Docker Hub → Kubernetes → Blue/Green → Service

## Docker Images

- `vardhan027/docker-version-demo:v1`
- `vardhan027/docker-version-demo:v2`

## Blue Environment

V1 runs with 3 replicas.

![Blue deployment](screenshots/04-blue-green-deployments.png)

## Green Environment

V2 runs with 3 replicas.

![Blue Green Pods](screenshots/05-blue-green-pods.png)

## Traffic Switch

Production traffic was switched from Blue V1 to Green V2 using:

```bash
kubectl patch service docker-demo-service -p '{"spec":{"selector":{"app":"docker-demo","version":"green"}}}'
