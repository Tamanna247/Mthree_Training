# KUBERNETES(WEEK-4,DAY-3)

After gaining knowledge in Kubernetes, we moved on to running the files, deploying applications, and managing Kubernetes and Pods.

In this document, we will see the flow of execution.

## **Flow of Execution**

### **1️⃣ Running the Deployment Script**
```sh
./scripts/deploy.sh
```

### **2️⃣ Execution Flow of `deploy.sh`**

#### **Step 1: Pre-checks & Minikube Setup**
- Checks if **Minikube** is running; starts it if needed.
- Enables necessary **addons** and configures **Docker**.

#### **Step 2: Build Docker Image**
- Builds the Docker image of **`k8s-master-app`** inside Minikube.

#### **Step 3: Namespace Setup (`namespace.yaml`)**
A **namespace** in Kubernetes is used to separate resources within a cluster. It helps to manage access to resources efficiently.

```yaml
apiVersion: v1
kind: Namespace
metadata:
    name: k8s-demo  # Name of the namespace
    labels:
         name: k8s-demo
         environment: demo
         app: k8s-master
```

#### **Step 4: ConfigMap Setup (`configmap.yaml`)**
- Stores **configuration data** separately from the application.
- Helps in better management of **environment variables and settings**.

#### **Step 5: Secrets Setup (`secret.yaml`)**
A **Secret** in Kubernetes is used to store **sensitive data** such as passwords, API keys, and authentication tokens.

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secrets
  namespace: k8s-demo
type: Opaque

data:
   SECRET_KEY: ZGV2LXNlY3JldC1rZXktMTIzNDU=
   DB_PASSWORD: cGFzc3dvcmQxMjM=
```

#### **Step 6: Persistent Storage Setup (`volumes.yaml`)**
- Ensures **storage for a Pod** to persist data across container restarts.

#### **Step 7: Deploy Application (`deployment.yaml`)**
- Creates multiple **replicas of Pods** to ensure availability.
- In this script, **2 replicas** are created to maintain high availability.

#### **Step 8: Service Exposure (`service.yaml`)**
- A **stable way to access Pods**, ensuring traffic is served only to healthy Pods.
- In cloud terms, it acts like a **Load Balancer**.
- Defines **NodePort, TargetPort, and Protocol**.

#### **Step 9: Autoscaling (`hpa.yaml`)**
HPA (**Horizontal Pod Autoscaler**) dynamically **scales the number of Pods** based on CPU and memory usage. It also removes unnecessary Pods.

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: k8s-master-hpa
  namespace: k8s-demo
spec:
  minReplicas: 1
  maxReplicas: 5
```

---

## **Main Application Code**

### **1️⃣ `app.py` (Application Code)**
- Runs a **Flask application** inside a Kubernetes Pod.
- Checks **metrics and health** of the application.
- Reads **ConfigMaps and Secrets**.

### **2️⃣ `Dockerfile` (Container Definition)**
- Defines dependencies using **`requirements.txt`**.
- Exposes **port 5000**, which is used in Kubernetes Service.
- Used in **`deploy.sh`** to **build and push the image**.

### **3️⃣ `requirements.txt` (Dependencies)**
```txt
Flask==2.2.3
Werkzeug==2.2.3
psutil==5.9.5
```
- Lists all required **Python packages** for the application.
- Installed inside the **Docker image**.

### **4️⃣ `test-app.sh` (Testing the Application)**
- Ensures **the app is running** in Kubernetes.
- Checks **Pod status** and validates API responses.
- Finds the **Service URL**.

```sh
kubectl get pods -n k8s-demo
kubectl get svc -n k8s-demo
curl -I http://localhost:5000/api/health
```

---

## **📌 Summary**
1️⃣ **Deployment starts with `deploy.sh`.**
2️⃣ **Creates Namespace, ConfigMaps, Secrets, and Volumes.**
3️⃣ **Deploys application using `deployment.yaml` (with 2 replicas).**
4️⃣ **Exposes application using `service.yaml`.**
5️⃣ **Enables autoscaling with `hpa.yaml`.**
6️⃣ **Runs `app.py` inside the Pods.**
7️⃣ **Validates deployment using `test-app.sh`.**

The Kubernetes cluster is now fully operational! 🚀