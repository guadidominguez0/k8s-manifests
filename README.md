# Despliegue de Sitio Web Estático en Kubernetes con Minikube
Este proyecto forma parte del trabajo práctico de la materia **Computación en la Nube**.

## Requisitos
- Minikube
- kubectl
- Docker (como driver de Minikube)
- Git
- Cuenta en GitHub

## Estructura del Repositorio
k8s-manifests/


├── debug/

│   └── debug.yaml

├── deployment/

│   └── deployment.yaml

├── service/

│   └── service.yaml

├── volume/

│   └── pv.yaml

│   └── pvc.yaml

└── README.md

## Pasos para realizar el proyecto
1. Crear los Repositorios y Clonar el Proyecto:
Abre una ventana de Power Shell y ejecuta los siguientes comandos:

cd ":/"

mkdir 0311AT


2. Para clonar ambos repositorios y tenerlos de forma local, dentro de la misma ventana de Power Shell”, ejecuta:

cd 0311AT

git clone https://github.com/guadidominguez0/static-website.git

git clone https://github.com/guadidominguez0/k8s-manifests.git


3. Iniciar Minikube con el Volumen montado

minikube delete

minikube start --mount --mount-string="C:/0311AT/static-website:/mnt/static"


4. Aplica los manifiestos

cd "C:/0311AT/k8s-manifests"

kubectl apply -f volume/pv.yaml

kubectl apply -f deployment/deployment.yaml

kubectl apply -f service/service.yaml


5. Acceder al sitio web

minikube service static-service
