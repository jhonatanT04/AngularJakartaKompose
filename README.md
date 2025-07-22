# 🐳 Proyecto con Minikube y Kompose

Este proyecto contiene una arquitectura desplegada en **Minikube** usando archivos generados por **Kompose**. La estructura incluye aplicaciones Angular, Jakarta y PostgreSQL, con scripts de backup y almacenamiento persistente.

## 📁 Estructura del Proyecto

.
├── angular-deployment.yaml
├── angular-service.yaml
├── jakarta-deployment.yaml
├── jakarta-service.yaml
├── postgres-deployment.yaml
├── postgres-service.yaml
├── pgdata-persistentvolumeclaim.yaml
├── pg-backup-cronjob.yaml
├── pg-backup-pvc.yaml
├── pg-backup-viewer.yaml
├── docker-compose.yaml
└── jakarta-postgres-app/

## 🚀 Instrucciones de uso

### 1. Iniciar Minikube

```bash
minikube start
