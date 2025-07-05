
# Week 5 - Task 4

## Task: Deploy a Microservice Application on AKS Cluster and Access it via Public Internet

### Objective
To containerize a simple Python Flask microservice, push the Docker image to Azure Container Registry (ACR), deploy it on an Azure Kubernetes Service (AKS) cluster, and access the service using a public IP.

---

## Step-by-Step Actions

### Step 1: Setup Microservice Code and Requirements

**Command(s):**

```bash
mkdir m-first-microservice
cd m-first-microservice
notepad app.py
notepad requirements.txt
notepad Dockerfile
```

**Screenshot:**  
![mkdir_cd_notepad_app](Images/imagestask4/mkdir_cd_notepad_app.png)

**Explanation:**  
Created the microservice project structure and files.

---

**Command:** *app.py content*  
**Screenshot:**  
![app_py_code](Images/imagestask4/app_py_code.png)

**Explanation:**  
Basic Flask app with one endpoint returning a message.

---

**Command:** *requirements.txt content*  
**Screenshot:**  
![requirements_txt_content](Images/imagestask4/requirements_txt_content.png)

**Explanation:**  
Declared Flask as the required dependency. 

---

**Command:** *Dockerfile content*  
**Screenshot:**  
![dockerfile_content](Images/imagestask4/dockerfile_content.png)

**Explanation:**  
Dockerfile to containerize the microservice. It copies the app.py file into the container, sets the working directory to /app, exposes port 5000, and copies the requirements.txt file into the container. The RUN command installs the required Flask package.

---

### Step 2: Build Docker Image

**Command:**

```bash
dir
```

**Screenshot:**  
![dir_initial](Images/imagestask4/dir_initial.png)

**Command:**

```bash
ren Dockerfile.txt Dockerfile
dir
```

**Screenshot:**  
![dir_rename_dockerfile](Images/imagestask4/dir_rename_dockerfile.png)

**Explanation:**  
Ensured Dockerfile is correctly named for Docker to recognize. 

---

**Command:**

```bash
docker build -t hello-microservice:v1.0 .
```

**Screenshot:**  
![docker_build_error](Images/imagestask4/docker_build_error.png)

**Explanation:**  
Error occurred due to misnamed Dockerfile (before fix). 

**Screenshot:**  
![docker_build_in_progress](Images/imagestask4/docker_build_in_progress.png)  
**Screenshot:**  
![docker_build_timing](Images/imagestask4/docker_build_timing.png)

**Explanation:**  
Successfully built Docker image after fixing the issue. The build process took approximately 2 minutes and 30 seconds. The Docker image is now named "hello-microservice:v1.0". 

---

### Step 3: Login to Azure and Push Image to ACR

**Command:**

```bash
az login --use-device-code
```


**Command:**

```bash
az acr login --name mymicroserviceacrbymanisha01
```

**Screenshot:**  
![acr_login_success](Images/imagestask4/acr_login_success.png)

---

**Command:**

```bash
docker tag hello-microservice:v1.0 mymicroserviceacrbymanisha01.azurecr.io/hello-microservice:v1.0
docker push mymicroserviceacrbymanisha01.azurecr.io/hello-microservice:v1.0
```

**Screenshot:**  
![docker_tag_push_acr](Images/imagestask4/docker_tag_push_acr.png)  
![docker_push_success](Images/imagestask4/docker_push_success.png)

**Explanation:**  
Tagged and pushed Docker image to Azure Container Registry. 

---

**Command:**

```bash
az acr repository list --name mymicroserviceacrbymanisha01 --output table
```

**Screenshot:**  
![acr_repo_list](Images/imagestask4/acr_repo_list.png)

---

### Step 4: Create and Configure AKS Cluster

**Command:**

```bash
az aks create ...
```

**Screenshot:**  
![aks_create_command](Images/imagestask4/aks_create_command.png)  
![aks_create_running](Images/imagestask4/aks_create_running.png)

---

**Command:**

```bash
az aks get-credentials --resource-group myMicroserviceRG --name myAKSCluster
kubectl get nodes
nano deployment.yaml
kubectl apply -f deployment.yaml
```

**Screenshot:**  
![aks_get_credentials_only](Images/imagestask4/aks_get_credentials_only.png)  
![aks_get_credentials_apply](Images/imagestask4/aks_get_credentials_apply.png)

**Explanation:**  
Connected to AKS cluster and deployed the microservice. 

---

**Command:** *deployment.yaml content*  
**Screenshot:**  
![deployment_yaml_content](Images/imagestask4/deployment_yaml_content.png)

---

### Step 5: Access the Application via Public IP

**Command:**

```bash
kubectl get pods
kubectl get service flask-service
```

**Screenshot:**  
![kubectl_get_pods_service](Images/imagestask4/kubectl_get_pods_service.png)

**Command:**

```bash
kubectl describe service flask-service
```

**Screenshot:**  
![kubectl_describe_service](Images/imagestask4/kubectl_describe_service.png)

**Explanation:**  
Confirmed service exposed via LoadBalancer with public IP. Used `kubectl describe` to get more information about the service. 

**Browser Screenshot:**  
![app_access_browser](Images/imagestask4/app_access_browser.png)

---

### Step 6: Manage Resources

**Command:**

```bash
kubectl delete pod -l app=flask-app
```

**Screenshot:**  
![kubectl_delete_pod](Images/imagestask4/kubectl_delete_pod.png)

**Command:**

```bash
kubectl get pods
```

**Screenshot:**  
![kubectl_get_pods](Images/imagestask4/kubectl_get_pods.png)

---

## Conclusion

Successfully built, containerized, and deployed a microservice Flask application on Azure Kubernetes Service and accessed it over the internet via LoadBalancer public IP. Managed resources using kubectl commands. 

