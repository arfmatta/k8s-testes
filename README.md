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

## Cluster de Airflow

Iniciar cluster com kind \
`kind create cluster`

Criar namespace Airflow \
`kubectl create namespace airflow`

Criar deployment Airflow com Helm Chart \
`helm repo add apache-airflow https://airflow.apache.org`

Criar pasta na S3

Fazer alterações no `myvalues.yml`

Iniciar Airflow com Helm \
`helm install airflow apache-airflow/airflow -f airflow/myvalues.yaml -n airflow --debug`

Aplicar port-forward \
`kubectl port-forward service/airflow-webserver 8080:8080 -n airflow`

Acessar URL localhost:8080 \
Senha: artur/admin (ou o que colocar no myvalues.yml)

Criar conexão para a AWS com nome my_aws \
Login: {aws_access_key_id} \
Password: {aws_secret_access_key}


