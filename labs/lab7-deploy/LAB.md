# Lab 7. Deploying you applications with Helm and Azure DevOps

## 1. Helm

Helm is the package manager for Kubernetes, it enables us to configure and deploy various Kubernetes resources using Helm Charts. Below are a few examples of charts that you can use to install applications into Kubernetes.

- [Keda](https://github.com/kedacore/charts)
- [Contour](https://github.com/bitnami/charts/tree/master/bitnami/contour/)
- [Jenkins](https://github.com/bitnami/charts/tree/master/bitnami/jenkins/)
- [Wordpress](https://bitnami.com/stack/wordpress/helm)
- [AAD Pod Identity](https://azure.github.io/aad-pod-identity/docs/getting-started/installation/#helm)
- [Application Gateway Ingress Controller](https://azure.github.io/application-gateway-kubernetes-ingress/setup/install-new/#install-ingress-controller-helm-chart)

Let's deploy the wordpress Helm Chart. First let's see what resources get deployed.

```powershell
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install wordpress --create-namespace --dry-run  -n wordpress bitnami/wordpress
```

This should print out all the resources this chart will create, followed by the instruction on how to access the wordpress installation once the deployment is done.

Let's deploy the Chart.

```powershell
helm install wordpress --create-namespace -n wordpress bitnami/wordpress
```

Once you have inspected the installed resources you can delete the installation by running the following command.

```powershell
helm delete wordpress -n wordpress
kubectl delete ns wordpress
```

We can also use Helm charts to define our own applications so can we dynamically apply configuration and deploy our applications.

Go through the following sections of the Chart Template Guide at the Helm [docs](https://helm.sh/docs/chart_template_guide/getting_started/):

- [Getting Started](https://helm.sh/docs/chart_template_guide/getting_started/)
- [Built-in Objects](https://helm.sh/docs/chart_template_guide/builtin_objects/)
- [Values Files](https://helm.sh/docs/chart_template_guide/values_files/)
- [Template Functions and Pipelines](https://helm.sh/docs/chart_template_guide/functions_and_pipelines/)
- [Flow Control](https://helm.sh/docs/chart_template_guide/control_structures/)
- [Variables](https://helm.sh/docs/chart_template_guide/variables/)
- [Debugging Templates](https://helm.sh/docs/chart_template_guide/debugging/)

## 2. Deploying an application using Helm and Azure DevOps

We will spend the rest of this lab trying to deploy a sample application to Kubernetes using Helm and Azure DevOps. The idea is that you deploy the application to a test environment and then on to a production environment.  

These environments need to to have their own resources and should be configured seperately.

The sample application to deploy can be found [here](./src). By modifying an environment variable called `WelcomeMessage`, you can change the welcome message displayed at the website.

[:arrow_backward: previous](../lab6-volumes/LAB.md)  [next :arrow_forward:](../lab8-troubleshooting/LAB.md)