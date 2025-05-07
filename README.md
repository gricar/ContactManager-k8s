# ContactManager-k8s

## Etapas para inicializar os pods

### Criar o volume
```
kubectl apply -f .\volumes
```

### Criar o Banco de Dados
```
kubectl apply -f .\mssql\secret.yaml
kubectl apply -f .\mssql
```

### Criar o RabbitMQ
```
kubectl apply -f .\rabbitmq\secret.yaml
kubectl apply -f .\rabbitmq
```

### Criar os Microserviços
```
kubectl apply -f .\api-gateway\services
```

### Criar a API Gateway
```
kubectl apply -f .\api-gateway
```
