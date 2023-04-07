# Section 3: DevOps with Docker and Kubernetes <br/> on Google Kubernetes Engine

<img
  src="https://user-images.githubusercontent.com/60389872/230453267-3e2fdf55-75ad-476f-aecb-8f8271093a24.png"
  style="display: inline-block; margin: 0 auto; width: 100%; height: 30em">

## Containers

### Create a new container

```bash
docker run -p 8080:8080 in28min/hello-world-rest-api:0.0.1.RELEASE
```

### URL

```url
http://localhost:8080/hello-world
```

## Kubernetes
### Create a new deployment in Kubernetes
```bash
kubectl create deployment hello-world-rest-api --image=in28min/hello-world-rest-api:0.0.1.RELEASE
```

deployment.apps/hello-world-rest-api created

```bash
kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
```

service/hello-world-rest-api exposed

```bash
kubectl scale deployment hello-world-rest-api --replicas=3
```

deployment.extensions/hello-world-rest-api scaled

```bash
kubectl delete pod hello-world-rest-api-58ff5dd898-6219d
```

pod "hello-world-rest-api-58ff5dd898-6219d" deleted
