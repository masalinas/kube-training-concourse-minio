fly -t training set-pipeline -p expressjs -c pipeline.yaml -l vars.template.yaml

fly -t training unpause-pipeline -p expressjs

fly -t training trigger-job --job expressjs/docker-build-and-push --watch
