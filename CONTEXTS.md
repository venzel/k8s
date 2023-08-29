# Namespaces & Contexts

```bash
# Obtém os namespaces
kubectl get ns

# Cria os namespaces de dev e prod
kubectl create ns dev
kubectl create ns prod

# Obtém os pods de um namespace
kubectl get pods -n=default
kubectl get pods -n=dev
kubectl get pods -n=prod

# Obtém o contexto atual setado
kubectl config current-context

# Verifica as configurações
kubectl config view

# Atacha um contexto a um namespace
kubectl config set-context dev --namespace=dev --cluster=kind-venzel --user=kind-venzel
kubectl config set-context prod --namespace=prod --cluster=kind-venzel --user=kind-venzel

# Altera o contexto
kubectl config use-context dev
kubectl config use-context prod
```

<div>
  <img align="left" src="https://imgur.com/k8HFd0F.png" width=35 alt="Profile"/>
  <sub>Made with 💙 by <a href="https://github.com/venzel">Enéas Almeida</a></sub>
</div>
