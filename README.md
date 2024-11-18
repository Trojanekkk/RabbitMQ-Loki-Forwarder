# rabbitmq-loki-forwarder
A simple Python script / app for pushing internal RabbitMQ messages from queue to the Loki instance.

For more details look for _Event Exchange Plugin_.

## Usage

### Docker

Run the app in the docker container with the default setup:

```
docker run -d ghcr.io/trojanekkk/rabbitmq-loki-forwarder:1.1.0
```

For almost 100% you will want to configure the app to make it work within your environment. To modify the default behaviour use environment variables. The following are allowed:

- `FORWARDER_LOKI_HOST` (defaults to _localhost_) - Hostname or IP address of the Loki server
- `FORWARDER_LOKI_PORT` (defaults to _3100_) - Port of the Loki server
- `FORWARDER_RABBITMQ_HOST` (defaults to _localhost_) - Hostname or IP address of the RabbitMQ server
- `FORWARDER_RABBITMQ_PORT` (defaults to _5672_) - Port of the RabbitMQ server
- `FORWARDER_RABBITMQ_USERNAME` (defaults to _guest_) - Username to authorize with the RabbitMQ server
- `FORWARDER_RABBITMQ_PASSWORD` (defaults to _guest_) - Password to authorize with the RabbitMQ server
- `FORWARDER_RABBITMQ_QUEUE` (defaults to _event_queue_) - Name of the Queue in the RabbitMQ server which is bound to the Event Exchange (check Event Exchange Plugin for more details) 
- `FORWARDER_APPLICATION_NAME` (defaults to _rabbitmq-loki-forwarder_) - Tag added to every message in the queue for filtering data in e.g. Grafana

For example:

```
docker run -d -e FORWARDER_LOKI_HOST=192.168.1.1 -e FORWARDER_LOKI_PORT=4321 ghcr.io/trojanekkk/rabbitmq-loki-forwarder:1.1.0
```

### Kubernetes (kubectl)

Run the app in the kubernetes cluster with the default setup:

```
kubectl apply -f https://raw.githubusercontent.com/Trojanekkk/RabbitMQ-Loki-Forwarder/refs/heads/main/k8s/deployment.yaml
kubectl apply -f https://raw.githubusercontent.com/Trojanekkk/RabbitMQ-Loki-Forwarder/refs/heads/main/k8s/configmap.yaml
```

For almost 100% you will want to configure the app to make it work within your environment. To modify the default behaviour clone or copy `k8s/configmap.yaml` file to your local filesystem, and modify the values accordingly. For detailed description check-out Docker usage (above). Then apply the configmap to your kubernetes cluster.

```
kubectl apply -f https://raw.githubusercontent.com/Trojanekkk/RabbitMQ-Loki-Forwarder/refs/heads/main/k8s/deployment.yaml
kubectl apply -f path/to/configmap/configmap.yaml
```

### Kubernetes (helm)

Not yet available