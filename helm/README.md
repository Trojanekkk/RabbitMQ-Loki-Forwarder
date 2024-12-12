
|Attribute|Default value|Description|
|-|-|-|
|replicaCount|1|The app is stateless. You can deploy as many replicas as needed. More replicas loweres DT|
|image.repository|ghcr.io/trojanekkk/rabbitmq-loki-forwarder|Repository from which the image will be pulled. You can use your own, private repository as well|
|image.tag|""|The tag of the container that will be deployed. Usefull when you want to stick to specific version|
|env[].name.FORWARDER_LOKI_HOST|loki|See Docker configuration for the description|
|env[].name.FORWARDER_LOKI_PORT|3100|See Docker configuration for the description|
|env[].name.FORWARDER_RABBITMQ_HOST|rabbitmq|See Docker configuration for the description|
|env[].name.FORWARDER_RABBITMQ_PORT|5672|See Docker configuration for the description|
|env[].name.FORWARDER_RABBITMQ_USERNAME|user|See Docker configuration for the description|
|env[].name.FORWARDER_RABBITMQ_PASSWORD|user|See Docker configuration for the description|
|env[].name.FORWARDER_RABBITMQ_QUEUE|event_queue|See Docker configuration for the description|
|env[].name.FORWARDER_APPLICATION_NAME|rabbitmq-loki-forwarder|See Docker configuration for the description|
|envSecretName|""|Overwrites all environemnt variables defined above. Use to pass them more securely|
