# Lab 1.  Environment setup

**Follow the following steps to setup your environment**

1. Follow the [Akskickstarter](https://github.com/Ibis-Software/AksKickStarters) instructions to setup your environment.
2. Install [Docker](https://www.docker.com/get-started)
3. Install [VS Code Kubernetes tools](https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-kubernetes-tools)
4. Setup access credentials for newly created cluster in step 1.

```powershell 
az aks get-credentails -n <clusterName> -g <clusterResourcegroupName>
```

[next :arrow_forward:](../lab2-exploring-k8s-api/LAB.md)