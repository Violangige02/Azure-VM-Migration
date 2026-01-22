## Project: Azure VM Migration (Nautilus DevOps)
**Task:** Provision a hardened Ubuntu 22.04 LTS instance for an incremental migration.

### 🛠️ Configuration Details:
* **VM Name:** xfusion-vm
* **Region:** eastus
* **Size:** Standard_B1s (1 vCPU, 1 GiB RAM)
* **Storage:** 30GB Standard HDD
* **Network:** Port 22 (SSH) open via Network Security Group (NSG).

### 🛡️ Security Decision:
I used an **SSH Key Pair** instead of a password. In 2026, password authentication is a high-risk liability. By using RSA keys, I ensured that only authorized administrators can access the `xfusion-vm`.

### ⚠️ Troubleshooting Log (Critical Fix):
* **Issue:** Received `ZonalAllocationFailed`. 
* **Fix:** I identified a regional capacity bottleneck. I resolved this by removing the specific Availability Zone constraint, allowing Azure to allocate resources across the broader `eastus` region.
<img width="1303" height="522" alt="fail to deploy VM" src="https://github.com/user-attachments/assets/82a360f9-e486-4067-a290-d88a71e7db12" />
