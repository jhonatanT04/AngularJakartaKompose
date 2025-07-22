# 🐳 Proyecto con Minikube y Kompose

Este proyecto contiene una arquitectura desplegada en **Minikube** usando archivos generados por **Kompose**. La estructura incluye aplicaciones Angular, Jakarta y PostgreSQL, con scripts de backup y almacenamiento persistente.

## Estructura del Proyecto

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
minikube start
### 2. Aplicar los archivos YAML

kubectl apply -f .
Asegúrate de estar en el directorio raíz del proyecto al ejecutar el comando anterior.

### 3. Verificar recursos


kubectl get all
### 4. Acceder a los servicios
Puedes exponer los servicios si estás usando Minikube local:

minikube service angular-service
minikube service jakarta-service

### 5. CronJob de backup
El archivo pg-backup-cronjob.yaml define una tarea automática para respaldar la base de datos PostgreSQL. Puedes verificarla así:

kubectl get cronjobs
kubectl get jobs
## 🛠 Herramientas utilizadas
Docker Compose: Configuración original del entorno

Kompose: Conversión de docker-compose.yaml a archivos de Kubernetes

Minikube: Cluster local de Kubernetes

kubectl: Herramienta de línea de comandos para interactuar con Kubernetes

## 📦 Conversión con Kompose
Si deseas convertir tu docker-compose.yaml nuevamente:

kompose convert

Esto generará los archivos YAML necesarios para desplegar en Kubernetes.

### Requisitos previos
Docker

Minikube

Kompose

Kubectl



### 📍 En el CASO de no encontrar las imagenes se puede realizar lo siguiente 
## Paso 1: Verifica si la imagen existe en Docker local

docker images

Si no aparece, necesitas construirla o descargarla.

## Paso 2A: Si tienes un Dockerfile, construye la imagen

docker build -t mi-imagen:latest .

Esto generará la imagen mi-imagen:latest localmente.

## Paso 2B: Si no tienes un Dockerfile, puedes descargar una imagen pública

docker pull nginx:latest

docker tag nginx:latest mi-imagen:latest

Reemplaza nginx:latest con la imagen base que desees.

## Paso 3: Cargar la imagen en Minikube

minikube image load mi-imagen:latest\

Esto copia la imagen local al entorno interno de Minikube, para que los Pods puedan usarla sin necesidad de un registry externo.


## Puedes verificar que el Pod está usando tu imagen correctamente con:


kubectl get pods

kubectl describe pod <nombre-del-pod>