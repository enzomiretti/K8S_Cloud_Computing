# 🚀 Despliegue local de sitio web estático con Minikube y Kubernetes

Este repositorio contiene un sitio web estático personalizado y los manifiestos necesarios para desplegarlo localmente usando Minikube y Kubernetes.

---

## 🌐 Requisitos previos

Antes de comenzar, asegúrate de tener instalados los siguientes programas y herramientas:

- **Minikube**: Para crear un clúster de Kubernetes localmente.
- **Docker**: Necesario para ejecutar los contenedores de Kubernetes.
- **Kubectl**: Herramienta de línea de comandos para interactuar con Kubernetes.
- **Git**: Para clonar los repositorios.

💡 **Recomendación:** usar **Minikube 1.24.x o superior** y **Docker 20.x o superior**.

⚠️ **Importante:**  
Si estás utilizando Minikube con el driver de Docker (`--driver=docker`), asegúrate de que Docker esté en ejecución en tu sistema.  
Minikube necesita Docker activo para crear los contenedores de Kubernetes.  
Si Docker no está corriendo, Minikube no podrá iniciar el clúster.

---

## 🚀 Pasos para ejecutar el entorno

### 1️⃣ Clonar los repositorios

Primero, clona los dos repositorios necesarios para este despliegue. Asegúrate de que ambos repositorios estén dentro de un directorio común:

```bash
git clone https://github.com/enzomiretti/K8S_Cloud_Computing.git
git clone https://github.com/enzomiretti/static-website.git
```

---

### 2️⃣ Iniciar Minikube con volumen montado

Para iniciar Minikube y montar el volumen que contiene el sitio web estático, usa el siguiente comando.  
⚠️ Asegúrate de cambiar la ruta `D:\ruta\completa\a\static-website` por la ubicación correcta de tu carpeta `static-website` en tu sistema:

```bash
minikube start --driver=docker --mount --mount-string="D:\ruta\completa\a\static-website:/mnt/web"
```

---

### 3️⃣ Aplicar los manifiestos

Aplica los manifiestos de Kubernetes para crear los recursos necesarios:

```bash
cd K8S_Cloud_Computing
kubectl apply -f pv/
kubectl apply -f pvc/
kubectl apply -f deployments/
kubectl apply -f services/
```

---

### 4️⃣ Verificar estado del pod

Verifica que los pods estén corriendo correctamente:

```bash
kubectl get pods
```

---

### 5️⃣ Acceder al sitio

Para acceder al sitio web desde tu navegador, usa el siguiente comando:

```bash
minikube service static-site-service
```

---

## ✅ Resultado esperado

Al acceder al servicio, podrás ver el contenido de tu sitio web personalizado, que debe mostrar el archivo `index.html` con sus respectivos estilos y scripts.

---
