**Autonomous Data Guard** functionality in **Oracle Autonomous Database**

---

##  **Autonomous Data Guard – Backup & Disaster Recovery for Autonomous Database**

###  **What is Autonomous Data Guard?**

Autonomous Data Guard provides **high availability** and **disaster recovery** for Oracle Autonomous Databases. It **monitors the primary database** (e.g., ATP demo) and **automatically fails over** to a standby instance in case of failure — **without any manual intervention**.

---

###  **How Failover Works**

* **Automatic Failover**:

  * No action needed from the user.
  * Seamless switch to the standby instance.
  * **Same** connection credentials, wallets, and URLs (APEX, OML, ORDS).
  * After failover:

    * Standby becomes new **Primary**.
    * A new **Standby** is automatically created.
* **Manual Failover**:

  * Triggered only when automatic failover fails.
  * User manually confirms the operation.
  * System recovers as much data as possible.

---

###  **Recovery Objectives**

| Scenario           | Recovery Time Objective (RTO) | Recovery Point Objective (RPO) |
| ------------------ | ----------------------------- | ------------------------------ |
| Automatic Failover | \~2 minutes                   | 0 minutes (no data loss)       |
| Manual Failover    | \~2 minutes                   | Up to 5 minutes (minimal loss) |

---

###  **High Availability Architecture**

* **Local Standby (Same Region)**:

  * Created in a **different availability domain** or physical machine.
  * Example: If Primary is in **Ashburn-AD1**, standby might be in **Ashburn-AD2**.
* **Cross-Region Standby**:

  * For **regional disaster recovery**.
  * Optional second peer added via **"Add Peer Database"**.
  * Remote standby appears in the **ADG tab** on OCI Console.

---

###  **How to Enable Autonomous Data Guard**

1. Navigate to your **Autonomous DB** in OCI Console.
2. Click **Upgrade to Autonomous Data Guard**.
3. Set Disaster Recovery Type to **Use Standby Database**.
4. Click **Submit** to provision the standby instance.
5. Wait until **peer state = Available**.
6. Optionally, click **Add Peer Database** for cross-region setup.

---

###  **Manual Switchover**

* Click **Switchover** on the console.
* Confirm the operation using the **database name**.
* Used for planned maintenance or testing.

---

###  **Key Benefits**

* **No additional configuration** post-failover.
* Maintains all existing **connectivity and authentication**.
* Resilient across **availability domains and regions**.
* Rapid recovery with **minimal or zero data loss**.
* Option for **cross-region failover** enhances business continuity.

---

