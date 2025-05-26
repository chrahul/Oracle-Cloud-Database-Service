 

## **Oracle Autonomous Database: Dedicated Infrastructure**

### **Overview: Deployment Choices**

![image](https://github.com/user-attachments/assets/f904cae7-c831-4d5b-bcc5-c7c1bf9fd490)


Oracle Autonomous Database offers two main deployment options:

1. **Serverless** – Fully managed by Oracle with no user control over infrastructure.
2. **Dedicated** – Runs on **Exadata Cloud Infrastructure** dedicated to a single customer, allowing more control, isolation, and customization.

---

## **1. Autonomous Database Serverless (Quick Contrast)**

* **Fully automated** by Oracle.
* You choose:

  * Workload type (Transaction Processing / Data Warehouse),
  * Region,
  * Compute & Storage base.
* **Elastic scaling**, automatic patching, and minimal admin overhead.
* Ideal for **simplicity and fast provisioning**.

---

## **2. Autonomous Database Dedicated**

### **Key Features**

* **Dedicated Exadata Infrastructure** (compute, storage, memory, network).
* Greater control over:

  * **Software update schedules**
  * **Versioning**
  * **Availability policies**
  * **Workload separation and density**
* **Customizable policies** per database or workload.

### **Ideal Use Cases**

* Enterprise-wide **Database-as-a-Service (DBaaS)**.
* **Workload consolidation** with guaranteed isolation.
* Regulatory or high-performance workloads.
* Running alongside **Exadata Database Service or ExaDB** on the same infrastructure.

---

## **3. Provisioning & Architecture**

### **Steps to Set Up**

1. **Subscribe** to Exadata Cloud Infrastructure (dedicated).
2. Provision **Autonomous VM Clusters (AVMC)**.
3. Create **Autonomous Container Databases (ACD)**.
4. User Databases are created inside ACDs.

> Each ACD can have distinct policies (updates, backups, availability, etc.)

### **Isolation & Security**

* Network path through **VCN (Virtual Cloud Network)** and **private subnets**.
* No public internet access by default.
* Encryption with **Transparent Data Encryption (TDE)**:

  * Automatic at-rest and in-transit encryption.
  * Transparent to authorized applications.
 
  ![image](https://github.com/user-attachments/assets/3edf3ee7-0765-4a83-aa4b-b6c39404962a)


---

## **4. Networking and Access**

### **Private Access Only**

* Defined within customer VCN.
* Subnet is **private** to ensure secure access.
* Supports **subnet peering, IPsec VPN, FastConnect** for on-premises integration.

![image](https://github.com/user-attachments/assets/adeaf628-d096-4933-a3e5-0df23bc3c807)


---

## **5. Autonomous Database on Exadata Cloud\@Customer**

### **Why Use Cloud\@Customer?**

* For customers needing:

  * **On-premise deployment**
  * **Data sovereignty**
  * **Low-latency**
  * **Legacy integrations**

### **Advantages**

* Autonomous capabilities **behind your firewall**.
* Up to:

  * **45x SQL read IOPS**
  * **40x SQL throughput**
  * **98% lower latency** than AWS RDS on Outposts.
* True **pay-per-use** pricing.
* OCI-based **patching, monitoring, autoscaling**.

### **Architecture**

* **Local Control Plane Servers**:

  * Manage requests and communication with Oracle Cloud.
* **Secure WebSocket Tunnel** to Oracle.
* **Remote Control Plane Servers**:

  * Handle telemetry, patching, cloud orchestration.

### **Network Design**

* High bandwidth: **10G, 25G, or 100G Ethernet**.
* **Active-standby configuration** for HA.
* Uses **RDMA over Converged Ethernet (RoCE)** for ultra-low latency.

### **Resilience**

* If **control plane connectivity** is lost:

  * Customer apps continue to access databases.
  * **Backups and autoscaling still work**.
  * OCI console/API management is temporarily unavailable.

---

## **6. Backup Options**

* Local NFS storage.
* Oracle Public Cloud object storage.
* **Zero Data Loss Recovery Appliance (ZDLRA)**.
* On-premise storage.

---

## **Conclusion**

**Autonomous Database Dedicated** and **Exadata Cloud\@Customer** offer:

* Enterprise-grade isolation, performance, and compliance.
* Flexibility for organizations with strict control and regulatory needs.
* Seamless management with Oracle Cloud automation for patching, updates, and backup.

---


