# External Secrets Demo

Sample project for showcasing the use of External Secrets Operator with Azure KeyVault and Kubernetes. AKS has a native integration with Azure KeyVault, which allows for seamless management of secrets in a Kubernetes environment. However, it is only for mounting external secrets as volumes. This project demonstrates how to use External Secrets Operator to manage secrets in a more flexible way, allowing for the use of secrets in environment variables and other configurations.

There are multiple ways of managing secrets in an application: _environment variables_, _mounted volumes_, _workload identity_ and _Kubernetes secrets_ to name a few. I like to keep secret management outside of the application and let them read them in using either mounted volumes or environment variables. Not all services has support for managed identity authentication. I want to use Azure KeyVault as a central place to manage secrets and use External Secrets Operator to manage the secrets in Kubernetes.

This project demonstrates how to use External Secrets Operator to manage secrets in a more flexible way, allowing for the use of secrets in environment variables and other configurations.

## Prerequisites

First we need to setup a `Kind` cluster with the following command:

```bash
kind create cluster --name external-secrets-demo
```

Then we need to install the `kubectl` command line tool. You can find the installation instructions [here](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/).

Next, we need to install the `Helm` command line tool. You can find the installation instructions [here](https://helm.sh/docs/intro/install/).

Finally, we install the `external-secrets-operator` using the following command:

```bash
helm repo add external-secrets https://charts.external-secrets.io
helm install external-secrets/external-secrets \
  --namespace external-secrets \
  --create-namespace \
```

## Setup Azure KeyVault

We need to create an Azure KeyVault and add some secrets to it. You can do this using the Azure CLI or the Azure Portal.

## Setup Azure KeyVault Access Policy
