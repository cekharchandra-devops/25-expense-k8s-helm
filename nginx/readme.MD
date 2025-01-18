# helm

Package Management for Kubernetes:
Helm is a package manager that simplifies Kubernetes deployments by templatizing manifest files, enabling easier management and versioning of Kubernetes applications.

Core Components:
Helm has three main components:

values.yaml: Defines configurable fields and their default values.

Chart.yaml: Contains metadata about the Helm chart, such as name, version, and description.

Templates: Kubernetes manifest files with placeholders for dynamic values.
Simplifies Configuration Management:

Helm externalizes frequently changing configurations into the values.yaml file. Developers can modify configurations there without altering the underlying Kubernetes manifest templates.

Ease of Deployment:
Helm provides simple commands to manage Kubernetes resources:

helm install: Deploys an application.
helm upgrade: Updates an application with new configurations.
helm uninstall: Deletes the deployed application.

Developer Productivity:
By centralizing configuration changes in values.yaml, Helm reduces errors and accelerates the deployment process.



## **1. Install Helm**
Before using Helm, ensure it is installed and configured:
```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

---

## **2. Chart Management Commands**

### **Search for Charts**
```bash
helm search hub <keyword>      # Search charts on Helm Hub
helm search repo <keyword>     # Search charts in your added repositories
```

### **Add a Helm Repository**
```bash
helm repo add <repo-name> <repo-url>
```
Example:
```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```

### **Update Repositories**
```bash
helm repo update
```

---

## **3. Deployment Commands**

### **Install a Chart**
```bash
helm install <release-name> <chart-name> --namespace <namespace> --create-namespace --values <values-file>
```
Example:
```bash
helm install my-app bitnami/nginx --namespace prod --create-namespace --values custom-values.yaml
```

### **Dry-Run and Debug Installation**
```bash
helm install <release-name> <chart-name> --dry-run --debug
```

### **Upgrade an Existing Release**
```bash
helm upgrade <release-name> <chart-name> --namespace <namespace> --values <values-file>
```
Example:
```bash
helm upgrade my-app bitnami/nginx --namespace prod --values updated-values.yaml
```

### **Rollback a Release**
```bash
helm rollback <release-name> <revision-number>
```
Example:
```bash
helm rollback my-app 2
```

### **Uninstall a Release**
```bash
helm uninstall <release-name> --namespace <namespace>
```

### **List Installed Releases**
```bash
helm list --all-namespaces
```

---

## **4. Template Management Commands**

### **Generate Kubernetes Manifests**
```bash
helm template <release-name> <chart-name> --values <values-file>
```

### **Lint a Chart**
```bash
helm lint <chart-path>
```

---

## **5. Debugging and Troubleshooting Commands**

### **Show Logs for Releases**
```bash
helm get all <release-name> --namespace <namespace>
```

### **Get Manifest of a Release**
```bash
helm get manifest <release-name> --namespace <namespace>
```

### **Test Release**
```bash
helm test <release-name> --namespace <namespace>
```

---

## **6. Repository Management Commands**

### **Package a Chart**
```bash
helm package <chart-path>
```

### **Push a Chart to a Repository**
```bash
helm push <chart.tgz> <repo-name>
```

---

## **7. EKS-Specific Helm Tips**

### **Use Kubernetes Context**
Ensure Helm is pointed to the correct EKS cluster:
```bash
kubectl config use-context <eks-cluster-context>
```

### **Namespace Management**
Deploy resources to specific namespaces:
```bash
helm install <release-name> <chart-name> --namespace <namespace> --create-namespace
```

### **Set Resource Limits **
Include resource limits in your `values.yaml` file:
```yaml
resources:
  requests:
    cpu: "500m"
    memory: "256Mi"
  limits:
    cpu: "1"
    memory: "512Mi"
```

---



