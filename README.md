Run Locust load test on Kubernetes

## How to use

### Quick Start

```sh
cd deploy
kubectl apply -f locust-ns.yaml \
            -f locust-master-deploy.yaml \
            -f locust-master-svc.yaml \
            -f locust-worker-deploy.yaml
```

### Settings

* change target host

```sh
sed -e 's#http://172.20.2.110#http://<Target Host>#g' locust-*-deploy.yaml
```

* scale up workers

```sh
kubectl scale deploy locust-worker --replicas=100
```

## How to build

```sh
sudo docker build -t unicell/locust -f docker/Dockerfile .
```
