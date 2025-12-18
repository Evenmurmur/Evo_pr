# Evo_pr

Проект для демонстрации CI/CD с использованием Docker + Docker compose, Kubernetes (Minikube) и GitHub Actions.

---

## Структура проекта

Evo_pr/
├─ docker/
│ └─ Dockerfile
├─ k8s/
│ ├─ deployment.yaml
│ └─ service.yaml
├─ scripts/
│ └─ deploy.sh
├─ .github/workflows/
│ └─ ci-cd.yml
├─ .gitignore
└─ README.md

---

**Сборка Docker-образа локально**
```
cd Evo_pr
docker build -t evo-pr:latest -f docker/Dockerfile .
```
Запуск Minikube
```
minikube start
```
Деплой приложения в Minikube
```
./scripts/deploy.sh
```
Проверка состояния деплоя
```
kubectl get deployments
kubectl get pods
kubectl get services
```
Просмотр приложения в браузере
```
minikube service nginx-pet
```

---

## CI/CD через GitHub Actions

**Pipeline выполняет:**

1. Сборку и пуш Docker-образа в GitHub Container Registry

2. Деплой в Kubernetes (можно на Minikube или другой кластер)


**Secrets для GitHub Actions:**

KUBE_CONFIG — конфиг Kubernetes в base64


**Запуск pipeline:**

Push в ветку main → автоматический запуск workflow.

**Скрипт деплоя:**

scripts/deploy.sh:
```
#!/bin/bash
set -e

# Применяем Kubernetes-манифесты
kubectl apply -f k8s/

# Ждем, пока деплой завершится
kubectl rollout status deployment/nginx-pet
```

Контакты

Автор: [Богдан]
Telegram: [@Evenlumber](https://t.me/Evenlumber])
Email: [Alihanovbogdan12345@gmail.com](mailto:Alihanovbogdan12345@gmail.com)
