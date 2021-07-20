# minikube velero credentials

- credentials-velero: velero credentials

# minikube healthcheck deployment example

- health.yaml: healthcheck deployment example

# minikube minio deployment

- namespace-minio.yaml: create minio namespace
- minio.yaml: minio deployment

# minikube concourse build and deploy pipeline example

- vars.template.yaml : credentials minikube
- pipeline.yaml : concourse pipeline

deploy the pipeline
fly -t training set-pipeline -p expressjs -c pipeline.yaml -l vars.template.yaml

unpause the pipeline
fly -t training unpause-pipeline -p expressjs

trigger first job pipeline
fly -t training trigger-job --job expressjs/docker-build-and-push --watch
