# Repo de testes do Kubernetes

Project started in September, 2021.

## Iniciar cluster com kind
`kind create cluster`

## Criar Namespace padrão
`kubectl create namespace podtest`

## Deploy de StatefulSet

Para criar o service com configuração local (ClusterIP) \
`kubectl apply -f podtest-sem-deployment/service.yaml -n podtest`

Para criar o service para cloud, com IP externo (LoadBalancer) \
`kubectl apply -f podtest/service.yaml -n podtest`

Criar StatefulSet \
`kubectl apply -f podtest/statefulset.yaml -n podtest`

Verificar objetos criados \
`kubectl get pods,pvc,svc -n podtest`

Acessar  local \
Aplicar port-forward \
`kubectl port-forward service/webserver 8080:8002 -n podtest` \
Acessar URL localhost:8080

Acessar na web/cloud: IP_EXTERNO:8002
