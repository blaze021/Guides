Here's a **plethora of Minikube customization commands**, organized by purpose — everything from setting CPUs, memory, drivers, runtimes, networking, mounts, to even experimenting with Kubernetes features.

---

## 🚀 **Start/Launch Customizations**

### 🧠 Resource Allocation

```bash
minikube start --cpus=4 --memory=8192 --disk-size=20g
```

### 💾 Specify Kubernetes Version

```bash
minikube start --kubernetes-version=v1.29.2
```

### 🧰 Specify Container Runtime

```bash
minikube start --container-runtime=containerd
minikube start --container-runtime=cri-o
```

### 🧪 Use a Specific Kubernetes Feature Gate

```bash
minikube start --feature-gates=TTLAfterFinished=true
```

### 🔧 Enable Addons on Start

```bash
minikube start --addons=ingress,dashboard,metrics-server
```

---

## 🧑‍💻 **Driver Customization**

### ☁️ Use a Specific VM Driver

```bash
minikube start --driver=docker
minikube start --driver=virtualbox
minikube start --driver=hyperv --hyperv-virtual-switch="ExternalSwitch"
```

### 🐳 Docker-Specific

```bash
minikube start --driver=docker --container-runtime=docker
```

---

## 🌐 **Networking Customization**

### 📦 Set Pod & Service CIDRs

```bash
minikube start --extra-config=kubeadm.pod-network-cidr=10.244.0.0/16
minikube start --extra-config=apiserver.service-cluster-ip-range=10.96.0.0/12
```

### 🛡️ Expose Ports

```bash
minikube start --ports=30000-32767
```

### 🔌 Custom DNS

```bash
minikube start --extra-config=kubelet.cluster-dns=10.96.0.10
```

---

## 🧱 **Volumes & Mounts**

### 📁 Mount Local Folders

```bash
minikube mount /host/folder:/mnt/folder
```

### 🔂 Mount On Start (Docker driver)

```bash
minikube start --mount --mount-string="/host/data:/data"
```

---

## 🧩 **Kubernetes Component Configuration**

### 🔁 Override Kubelet Settings

```bash
minikube start --extra-config=kubelet.authentication.anonymous.enabled=false
```

### ⚙️ Override Controller Manager/ Scheduler/ API Server

```bash
minikube start \
  --extra-config=controller-manager.horizontal-pod-autoscaler-use-rest-clients=true \
  --extra-config=scheduler.bind-address=0.0.0.0 \
  --extra-config=apiserver.enable-admission-plugins=NamespaceLifecycle,LimitRanger
```

---

## 🧪 **Experimental / Advanced Flags**

### 🛠️ Enable Systemd Cgroup Driver (containerd/cri-o)

```bash
minikube start --extra-config=kubelet.cgroup-driver=systemd
```

### 📊 Set Audit Policy

```bash
minikube start --extra-config=apiserver.audit-log-path=- --extra-config=apiserver.audit-log-maxage=30
```

### 🧬 Custom Image Repository Mirror

```bash
minikube start --image-mirror-country=CN
```

---

## 🎛️ **Post-Start Operations**

### 🟢 Enable Addons After Start

```bash
minikube addons enable metrics-server
minikube addons enable ingress
```

### 🔄 Restart With New Config

```bash
minikube stop
minikube start --cpus=6 --memory=12288
```

---

## 📦 **Cache & Images**

### 🗃️ Cache Images Before Use

```bash
minikube cache add nginx busybox alpine
```

### 🔍 Load Docker Images into Minikube

```bash
minikube image load my-custom-image:latest
```

---

## 🧼 **Cleanup & Reset**

```bash
minikube delete
minikube delete --all --purge
```

---

## 🐳 **Docker Inside Minikube (Docker Driver)**

```bash
eval $(minikube docker-env)
docker build -t myapp:latest .
minikube image load myapp:latest
```

---

If you're doing this frequently, consider aliases or wrapping these commands into a shell script for your specific environment.

Want help creating a reusable script for this setup?


```
kubectl proxy --address='0.0.0.0' --accept-hosts='^.*$' &
```
