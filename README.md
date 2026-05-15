# argocd-demo

Repository pubblico con i manifest per la demo ArgoCD.
ArgoCD clona questo repo direttamente, senza bisogno di credenziali.

## Struttura

```
argocd-demo/
├── apps/
│   └── demo/
│       ├── deployment.yaml      # Deployment nginx, 10 repliche
│       ├── service.yaml         # Service ClusterIP
│       └── daemonset.yaml       # DaemonSet (1 Pod per nodo)
└── argocd/
    ├── project-platform-demo.yaml     # AppProject ristretto
    ├── application-failing.yaml       # Application destinazione `prod-demo` (fallisce)
    └── application-fixed.yaml         # Application destinazione `default` (funziona)
```

## Uso

I manifest sotto `apps/demo` sono il workload che ArgoCD deploya. I manifest sotto `argocd/` sono gli oggetti ArgoCD da applicare con `kubectl apply -n argocd -f ...` per orchestrare la demo.

Tutte le Application puntano a `https://github.com/Miky186/argocd-demo.git` con `path: apps/demo` e `targetRevision: main`.
