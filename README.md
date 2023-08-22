# k8s

## Kind

### Instalação

Documentação: https://kind.sigs.k8s.io/

```bash
# Baixa o binário
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64

# Torna executável
chmod +x ./kind

# Move o kind para /usr/local/bin
sudo mv ./kind /usr/local/bin/kind
```

### Kind.yaml

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
    - role: control-plane
    - role: worker
    - role: worker
    - role: worker
```

### Criação do cluster

```bash
# Cria o cluster
kind create cluster --config=k8s/kind.yaml --name=venzel

# Altera o contexto
kubectl cluster-info --context kind-venzel
```

### Deleção do cluster

```bash
kind delete clusters venzel
```

## Instalação do Kubectl

Documentação: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

## Comandos Kubectl

```bash
# Verificar os clusters
kubectl config get-clusters

# Alterar o contexto
kubectl config use-context k3d-k3s-default

# Verifica os namespaces disponíveis
kubectl get ns

# Verifica os nós
kubectl get nodes

# Verifica os pods
kubectl get pods

# Verifica os services
kubectl get svc
```

<div>
  <img align="left" src="https://imgur.com/k8HFd0F.png" width=35 alt="Profile"/>
  <sub>Made with 💙 by <a href="https://github.com/venzel">Enéas Almeida</a></sub>
</div>
