# Pipoca App

![Pipeline](https://github.com/dellabeneta/pipoca-app/actions/workflows/main.yaml/badge.svg)

Uma aplicação web simples que exibe uma foto da gata Pipoca e o nome do contêiner em que está sendo executada. O projeto foi desenvolvido com Python e Flask, e está configurado para deploy contínuo em um cluster Kubernetes (K3s).

## Funcionalidades

- Exibe uma página web estilizada com a foto da gata Pipoca.
- Mostra o hostname do contêiner que atendeu a requisição.
- Backend em Python com Flask.
- Pronto para rodar em Docker e Kubernetes.
- Pipeline de CI/CD com GitHub Actions para build e deploy automáticos.

## Começando

### Pré-requisitos

- Python 3.9 ou superior
- Docker (opcional)
- Kubernetes/k3s (opcional)

### Instalação Local

```bash
git clone https://github.com/dellabeneta/pipoca-app.git
cd pipoca-app
pip install -r app/requirements.txt
python app/main.py
```

Acesse em [http://localhost:8080](http://localhost:8080)

### Usando Docker

```bash
docker build -t pipoca-app .
docker run -p 8080:8080 pipoca-app
```

### Deploy no Kubernetes

```bash
kubectl apply -f k3s/namespace.yaml
kubectl apply -f k3s/deployment.yaml
kubectl apply -f k3s/service.yaml
```

A aplicação estará disponível na porta `30087` do cluster.

## Estrutura do Projeto

```
.
├── .github
│   └── workflows
│       └── main.yaml
├── app
│   ├── main.py
│   ├── requirements.txt
│   ├── static
│   │   └── images
│   │       └── cat.png
│   └── templates
│       └── index.html
├── Dockerfile
├── k3s
│   ├── deployment.yaml
│   ├── namespace.yaml
│   └── service.yaml
├── nuke.sh
└── README.md
```

## Como Funciona

1. O usuário acessa a aplicação através do navegador.
2. O backend em Flask renderiza a página `index.html`.
3. A página exibe a imagem da gata Pipoca e o hostname do contêiner obtido via Python.

## Scripts Úteis

**nuke.sh**: Script para limpeza completa do ambiente Docker (contêineres, imagens, volumes e redes).

```bash
chmod +x nuke.sh
./nuke.sh
```