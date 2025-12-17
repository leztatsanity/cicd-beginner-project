# ci-cd-final-project

## 🚀 Project Overview
This project, titled **ci-cd-final-project**, demonstrates a complete **CI/CD Pipeline** using **GitHub Actions** for Continuous Integration (CI) and **Red Hat OpenShift Tekton** for Continuous Delivery (CD).

---

## 🛠️ Project Structure

* `app.py`: A simple Python application.
* `test_app.py`: Unit tests for the application.
* `.github/workflows/main.yml`: GitHub Actions configuration.
* `/tekton`: Folder containing Tekton Tasks and Pipeline definitions.

---

## ⚙️ Setup Instructions

### 1. Continuous Integration (GitHub)
1. Create a new repository on GitHub named **ci-cd-final-project**.
2. Push this project code to the repository.
3. Navigate to the **Actions** tab on GitHub to see the "CI Pipeline" running.
    - **Linting:** Checks code for formatting errors.
    - **Testing:** Runs unit tests to ensure code quality.

### 2. Continuous Delivery (OpenShift Tekton)
Before running the pipeline in the **ci-cd-final-project**, ensure the **OpenShift Pipelines Operator** is installed.

**Step A: Create Storage**
Create a Persistent Volume Claim (PVC) to allow Tekton to store data:
```bash
oc apply -f - <<EOF
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: tekton-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
EOF
