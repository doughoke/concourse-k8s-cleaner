# concourse-k8s-cleaner
Provides a Kubernetes CronJob to clean up stalled workers of concourse that are built using helm stable/concourse

### **WIP**

## Genesis
Inspired by Concourse, Helm Chart and SRE oxygen-mask

https://github.com/concourse/concourse

https://github.com/helm/charts/tree/master/stable/concourse

https://github.com/concourse/oxygen-mask

## Defaults
Runs every 10 minutes (this can be changed in cron syntax in K8SConcourseCronJob.yaml)

Requires secrets to be set for cron container to access concourse with fly and run fly worker 

| Key | Description | Default Value |
| --- | --- | -- |
| `atc_url` | URL for ATC (should be what you use to login in a browser) | http://localhost |
| `concourse_team` | The team that you wish to list workers for | main |
| `concourse_user` | The user to login concourse with | test |
| `concourse_pwd` | The password for the user to login concourse with | test |
| `k8s_concourse_namespace` | The namespace concourse is running in | default |
  
These can be changed by Base64 encrypting your values and replacing them in k8sConcourseCronJobSecrets.yaml

## How To Run
Assumes you have concourse installed in kubernetes leveraging Helm Chart and you have access to kubernetes cluster
```
git clone https://github.com/doughoke/concourse-k8s-cleaner.git
update K8SConcourseCronJobSecrets.yaml with your values
kubectl apply --recursive --filename . --namespace default
```
## TODO
Create as a helm chart

