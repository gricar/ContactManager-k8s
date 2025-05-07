# Contact Manager K8s

### Descrição
> É uma aplicação em arquitetura de microsserviços, utilizando o Kubernetes para gerenciamento de conteinerização, orquestração e escalabilidade.

<details>
  <summary><strong>Inicializar os pods</strong></summary>

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
  kubectl apply -f .\api-gateway\services\create-contact
  kubectl apply -f .\api-gateway\services\delete-contact
  kubectl apply -f .\api-gateway\services\update-contact
  kubectl apply -f .\api-gateway\services\persistence-contact
  ```
  
  ### Criar a API Gateway
  ```
  kubectl apply -f .\api-gateway
  ```
</details>

<details>
  <summary><strong>Comandos básicos de Kubernetes</strong></summary>

  ### Visualizar
  ```
  kubectl get secrets

  kubectl get pods,deployment,svc
  
  kubectl get deployment,svc -l app=contact-api
  
  kubectl describe deployment/api-gateway
  
  kubectl logs pods/contact-persistence-9b887cd7d-htr5r --tail=50
  ```
  
  ### Interação
  ```
  kubectl apply -f deployment.yaml
  
  kubectl delete deployment/api-gateway
  
  kubectl delete deployment,svc -l app=contact-api

  kubectl delete configmaps --all
  
  # Editar sem rebuildar a imagem
  kubectl edit configmap api-gateway-config
  
  kubectl rollout restart deployment api-gateway
  ```
</details>
