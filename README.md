# k3s.infrastructure
K3S Infrastructure

- Basic setup of the cluster before we can start building stuff on it
1. Install argocd
  - Run ArgoCD in insecure mode, we handle TLS termination in Traefik in item 3 of the main list
1. Install certmanager through argocd
2. Secure ArgoCD through argocd
  - Run a certmanager issuer in the argocd namespace
  - Run a staging issuer too, if you want
  - Run ingress for argocd that uses the certmanager issued cert for TLS
3. Expose the traefik dashboard
  - Deploy a certmanager issuer in the kube-system namespace
  - Deploy a staging issuer too, if you want
  - Create a kubernetes service to expose the dashboard
  - Create an ingress resource that uses the certmanager issued TLS cert
