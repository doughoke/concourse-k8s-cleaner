# concourse-k8s-cleaner
Provides a Kubernetes CronJob to clean up stalled workers of concourse that are built using helm stable/concourse

### WIP

## Genesis
Inspired by Concourse, Helm Chart and SRE oxygen-mask

https://github.com/concourse/concourse

https://github.com/helm/charts/tree/master/stable/concourse

https://github.com/concourse/oxygen-mask

## Defaults
Runs every 10 minutes (this can be changed in cron syntax in K*SConcourseCronJob.yaml)

Requires secrets to be set for cron container to access concourse with fly and run fly worker 
  atc_url: http://localhost
  concourse_team: main
  concourse_user: test
  concourse_pwd: test
  k8s_concourse_namespace: default

  These can be changed by Base64 encrypting your values and replacing them in k8sConcourseCronJobSecrets.yaml

## How To Run
Assumes you have concourse installed in kubernetes leveraging Helm Chart and you have access to kubernetes cluster

git clone ...
update K8SConcourseCronJobSecrets.yaml with your values
kubectl apply --recursive --filename . --namespace default

##TODO
Create as a helm chart

