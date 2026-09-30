# Kubernetes Practice (K8S)

Hands-on Kubernetes practice: local clusters with **kind**, example manifests, an nginx deployment, a sample online shopping app, and simple notes on how Kubernetes works.

---

## Repository Structure

```
Kubernetes-practice-K8S/
├── kind-cluster/               # kind cluster configuration files
├── nginx/                      # nginx deployment / service manifests
├── online_shopping_app/        # sample multi-component app deployed on Kubernetes
├── practice/                   # practice manifests and experiments
└── kubernetes_architecture.md  # beginner-friendly Kubernetes architecture notes
```

| Folder / File | Purpose |
|---|---|
| `kind-cluster/` | Create a local multi-node Kubernetes cluster using kind (Kubernetes in Docker) |
| `nginx/` | Deploy and expose nginx to practice Pods, Deployments and Services |
| `online_shopping_app/` | Deploy a sample shopping application on the cluster |
| `practice/` | Small exercises to try out Kubernetes objects |
| `kubernetes_architecture.md` | Plain-English explanation of control plane, worker node components, Pods, Services, Volumes, Namespaces and Ingress |

---

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) (running)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [kind](https://kind.sigs.k8s.io/docs/user/quick-start/)
- Git

Windows users: use WSL2 and enable Docker Desktop's WSL integration for your Linux distro.

Verify your tools:

```bash
docker ps
kubectl version --client
kind version
```

---

## Getting Started

**1. Clone the repository**

```bash
git clone https://github.com/imVikash-ai/Kubernetes-practice-K8S.git
cd Kubernetes-practice-K8S
```

**2. Create a kind cluster**

```bash
kind create cluster --name my-cluster
# or, using a config file from this repo:
# kind create cluster --name my-cluster --config kind-cluster/<config-file>.yaml
```

**3. Confirm kubectl is connected**

```bash
kubectl config current-context    # should show kind-my-cluster
kubectl get nodes
```

**4. Apply a manifest**

```bash
kubectl apply -f nginx/
kubectl get pods
kubectl get svc
```

**5. Clean up**

```bash
kubectl delete -f nginx/
kind delete cluster --name my-cluster
```

---

## Useful kubectl Commands

```bash
kubectl get pods,svc,deploy          # list common resources
kubectl describe pod <pod-name>      # detailed info and events
kubectl logs <pod-name>              # view logs
kubectl exec -it <pod-name> -- sh    # shell into a pod
kubectl port-forward svc/<svc-name> 8080:80
kubectl scale deploy <name> --replicas=3
kubectl rollout status deploy/<name>
```


## Topics Covered

- Kubernetes architecture (control plane and worker nodes)
- Pods, Deployments, ReplicaSets
- Services and networking
- Namespaces, Volumes, Ingress
- Local clusters with kind
- Deploying a multi-component application

---

## Learning Resources

- [Kubernetes Documentation](https://kubernetes.io/docs/home/)
- [kind Documentation](https://kind.sigs.k8s.io/)
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

---

## Author

**Vikash** ([@imVikash-ai](https://github.com/imVikash-ai))

Feel free to open an issue or pull request if you have suggestions.