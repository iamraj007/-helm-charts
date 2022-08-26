# Helm Charts for AKS Kyverno Policies

[Introduction to kyverno](https://kyverno.io/docs/introduction/)
Kyverno (Greek for “govern”) is a policy engine designed specifically for Kubernetes.

Kyverno allows cluster administrators to manage environment specific configurations independently of workload configurations and enforce configuration best practices for their clusters. Kyverno can be used to scan existing workloads for best practices, or can be used to enforce best practices by blocking or mutating API requests.


## How Kyverno works:
Kyverno runs as a dynamic admission controller in a Kubernetes cluster. Kyverno receives validating and mutating admission webhook HTTP callbacks from the kube-apiserver and applies matching policies to return results that enforce admission policies or reject requests.

## Install steps for Kyverno on cluster (via single yaml file or you can also use helm chart)
```sh
   https://kyverno.io/docs/installation/ 
   kubectl create -f https://raw.githubusercontent.com/kyverno/kyverno/main/config/install.yaml 
```

## Install Kyverno via Helm
```sh
   helm repo add kyverno https://kyverno.github.io/kyverno/
   helm repo update
   helm install kyverno kyverno/kyverno -n kyverno --create-namespace
```

Kyverno installation and intraction with API server:
![kyverno-installation](https://user-images.githubusercontent.com/47947075/186667375-646a2697-6da8-4bd0-b754-9cd9f1bbab6c.png)

- The Webhook handles AdmissionReview requests from the Kubernetes API server
- Monitor component creates and manages required configurations
- The PolicyController watches policy resources and initiates background scans based on the configured scan interval
- The GenerateController manages the lifecycle of generated resources
