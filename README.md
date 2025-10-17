# 🚀 Employee API DevOps Project

A **complete DevOps learning project** built with **Java (Spring Boot)**, **Docker**, **Jenkins**, and **Kubernetes** — designed for hands-on CI/CD learning.

---

## 🧩 Tech Stack

| Component | Technology |
|------------|-------------|
| Language | Java 17 |
| Framework | Spring Boot |
| Build Tool | Maven |
| CI | Jenkins |
| Containerization | Docker |
| CD / Orchestration | Kubernetes (Minikube) |
| Registry | Docker Hub |
| Exposure | Kubernetes Ingress (NGINX) |

---

## ⚙️ Project Overview

**Goal:** Automate build → containerize → deploy → expose pipeline using Jenkins + K8s.

**Workflow:**
```
GitHub → Jenkins (CI) → Docker Hub → Kubernetes (CD) → Ingress → Browser
```

---

## 📁 Folder Structure

```
employee-api-devops/
├── src/
│   └── main/java/com/example/employee/
│       ├── Employee.java
│       ├── EmployeeRepository.java
│       ├── EmployeeController.java
│       └── EmployeeApiApplication.java
│
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
│
├── pom.xml
├── Dockerfile
└── Jenkinsfile
```

---

## 🧱 Application Summary

A simple **Employee REST API** with CRUD endpoints:

| Method | Endpoint | Description |
|--------|-----------|-------------|
| GET | `/employees` | List all employees |
| POST | `/employees` | Create a new employee |
| PUT | `/employees/{id}` | Update an employee |
| DELETE | `/employees/{id}` | Delete an employee |

Database: **H2 in-memory**

---

## 🧰 Prerequisites

Ensure you have these installed locally:

- ☕ Java 17+
- 🐳 Docker
- 🧩 Minikube
- ⚙️ kubectl
- 🧱 Maven
- 🧠 Jenkins (running locally)
- 🌐 Git

---

## 🚀 Local Build & Run

1. **Build the JAR**
   ```bash
   ./mvnw clean package
   ```

2. **Run locally**
   ```bash
   java -jar target/employee-api-1.0.0.jar
   ```

3. Open:  
   👉 http://localhost:8080/employees

---

## 🐳 Docker Build

```bash
docker build -t maroof49/employee-api .
docker push maroof49/employee-api
```

---

## ☸️ Deploy on Minikube

1. Start Minikube:
   ```bash
   minikube start
   minikube addons enable ingress
   ```

2. Deploy:
   ```bash
   kubectl apply -f k8s/
   ```

3. Add host entry:
   ```bash
   echo "$(minikube ip) employee.local" | sudo tee -a /etc/hosts
   ```

4. Access in browser:
   👉 http://employee.local/employees

---

## 🔄 Jenkins Pipeline (CI/CD)

**Jenkinsfile stages:**

| Stage | Description |
|--------|-------------|
| Checkout | Pulls code from GitHub |
| Build | Runs Maven build |
| Docker Build & Push | Builds Docker image & pushes to Docker Hub |
| Deploy to K8s | Applies manifests to Kubernetes |

### Jenkins Setup

1. Open Jenkins → **New Item → Pipeline**
2. In "Pipeline script from SCM":
   - SCM: Git
   - Repo URL: `https://github.com/maroof49/employee-api-devops.git`
3. Add Docker Hub credentials:
   - ID: `dockerhub-credentials-id`
   - Type: Username & Password
4. Save & **Build Now**

---

## 🧠 CI/CD Flow Summary

1. You commit code to GitHub (manual Jenkins build for now).
2. Jenkins:
   - Builds app using Maven
   - Creates Docker image
   - Pushes image to Docker Hub (`maroof49/employee-api`)
   - Deploys new image to Minikube via `kubectl`
3. Ingress exposes the app at:  
   **http://employee.local**

---

## 🧹 Clean Up

```bash
kubectl delete -f k8s/
minikube stop
```

---

## 🧠 Learning Outcomes

✔️ Full CI/CD pipeline setup  
✔️ Docker image build & push  
✔️ Kubernetes deployment automation  
✔️ Ingress-based service exposure  
✔️ Hands-on Jenkins integration  

---

## 💡 Next Steps (Advanced)

- Add **GitHub Webhooks** to trigger builds automatically  
- Integrate **SonarQube** for code quality  
- Add **Prometheus + Grafana** for monitoring  
- Use **Helm charts** for packaging  
- Add **ArgoCD** for GitOps deployment  

---

## 👨‍💻 Author

**Maroof Siddiqui**  
DevOps Engineer | Automation Enthusiast  
Docker Hub: [maroof49](https://hub.docker.com/u/maroof49)  
GitHub: [maroof49](https://github.com/maroof49)
