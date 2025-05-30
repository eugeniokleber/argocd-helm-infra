# Implantação do nginx-webserver com Helm + Argo CD

Este projeto demonstra como empacotar um Helm chart localmente e implantá-lo usando o Argo CD.

**Estrutura de diretórios**

```bash
.
├── apps
│   └── nginx-webserver
│       ├── application.yaml
│       ├── charts
│       │   └── nginx-webserver-0.1.0.tgz
│       ├── Chart.yaml
│       └── values.yaml
└── README.md

```

**1. Gerar o pacote do Helm Chart**

```bash
cd apps/nginx-webserver/

# Gerar o pacote .tgz no diretório charts na raiz
helm package . --destination ../../charts
```

**2. Testar o chart sem o argo localmente**

```bash
# Renderize os manifests usando helm template:
helm template teste charts/nginx-webserver-0.1.0.tgz

# Instale o Chart no cluster Kubernetes:
helm install teste charts/nginx-webserver-0.1.0.tgz
```

**3. Validando a instalação e listando os services**

```bash
# Listar os services:
kubectl get svc

# Ver detalhes do service criado (exemplo com nome teste):
kubectl get svc teste -o wide
```
**4. Gerenciar a release**

```bash
# Listando as releases instaladas
helm list

# Desinstalar uma release
helm uninstall teste
```
