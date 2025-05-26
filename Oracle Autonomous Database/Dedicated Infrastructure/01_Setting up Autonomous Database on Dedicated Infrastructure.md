**step-by-step flow summary** of the lesson on **provisioning an Autonomous Database on Dedicated Exadata Infrastructure** 

---

###  ** Setting up Autonomous Database on Dedicated Infrastructure**

![image](https://github.com/user-attachments/assets/b91c12a8-8211-41ec-8b80-250b1137fe51)


---

#### **1. Sign In and Prepare for Provisioning**

* Log in to Oracle Cloud as **Fleet Administrator or Network Administrator**.
* Go to **Autonomous Database Service** in the OCI Console.
* Ensure you're in the correct **fleet compartment**.

---

#### **2. Provision Autonomous Exadata Infrastructure**

* **Navigate to**: Autonomous Exadata Infrastructure → Click **Create**.
* **Set parameters**:

  * **Display Name**
  * **Availability Domain**
  * **Shape** (e.g., Quarter Rack, 92 OCPUs)
  * **Subnet**
  * **License Type**
* **Maintenance Window** (optional):

  * Change default schedule if needed (e.g., Quarterly, 1st Sunday, 12–4 AM UTC).
* Click **Create**.

---

#### **3. Create Network Architecture**

* Create a **VCN** with CIDR `10.0.0.0/16`.
* Add **two Security Lists**:

  * For **Exadata subnet**
  * For **Application subnet**
* Define **custom route tables**:

  * **Application Subnet** → Route to **Internet Gateway** (`0.0.0.0/0`)
  * **Exadata Subnet** → Default (no internet)
* **Subnets**:

  * Exadata Subnet: `10.0.0.0/24`
  * Application Subnet: `10.0.1.0/24`

---

#### **4. Provision Autonomous Container Database (ACD)**

* Log in as **Fleet Administrator**.
* Navigate to: Autonomous Transaction Processing → **Autonomous Container Database**.
* Click **Create Autonomous Container Database**.
* Set:

  * **Release Update (RU)** or patches
  * **Maintenance Schedule**
  * **Backup Retention Policy** (up to 60 days)
* Click **Create** to deploy ACD.

---

#### **5. Provision Autonomous Database (ADB) on Dedicated Infrastructure**

* Log in as **Database User**.
* Go to:

  * **Autonomous Transaction Processing** or
  * **Autonomous Data Warehouse**
* Click **Create Autonomous Database**.
* Set:

  * **Name**
  * **Workload Type** (TP or DW)
  * **Infrastructure Type** → Choose **Dedicated**
  * **Compartment** → Choose **Fleet Compartment**
  * **Select ACD** from the list
* Click **Create** to provision.

---

###  Additional Notes:

* All provisioning is done within your **compartment and network model**.
* **Bastion hosts** may be added if internet access is needed securely.
* Retain flexibility by managing **patching**, **backup**, and **maintenance** settings.
* Infrastructure supports **latency-sensitive apps**, **custom patching**, and **manual version control**.

---


