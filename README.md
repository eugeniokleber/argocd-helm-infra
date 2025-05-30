# Implantação do nginx-webserver com Helm + Argo CD

Este projeto demonstra como empacotar um Helm chart localmente e implantá-lo usando o Argo CD.

---

## Estrutura de diretórios
.
├── apps
│   └── nginx-webserver
│       ├── application.yaml
│       ├── charts
│       │   └── nginx-webserver-0.1.0.tgz
│       ├── Chart.yaml
│       ├── templates
│       │   ├── deployment.yaml
│       │   ├── hpa.yaml
│       │   ├── ingress.yaml
│       │   └── service.yaml
│       └── values.yaml
└── README.md


---

## 1. Exemplo de como empacotar o Helm chart

```bash
cd apps/nginx-webserver/

# Gerar o pacote .tgz no diretório charts na raiz
helm package . --destination ../../charts

# Testar o chart sem o argo
helm template teste charts/nginx-webserver-0.1.0.tgz

helm install teste charts/nginx-webserver-0.1.0.tgz

# Liste os services
kubectl get svc

# Achar o service, por exemplo, teste, execute:
kubectl get svc teste -o wide

# Listando as releases instaladas
helm list

# Removendo as releaser instaladas
helm uninstall teste
