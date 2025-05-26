
---

# Tutorial: Introduction to Oracle Autonomous Database Serverless

##  Overview

Oracle Autonomous Database Serverless is a fully managed, high-performance cloud database offering that uses **machine learning and automation** to handle routine database tasks. It supports **auto-scaling**, **provisioning**, **resource management**, and **monitoring** without manual intervention. This makes it an ideal choice for cloud-native applications requiring elasticity, reliability, and simplicity.

---

##  What You Will Learn

In this tutorial, we will cover:

1. What is Autonomous Database Serverless?
2. Key Features: Compute & Storage Scaling
3. Understanding Auto Scaling
4. Step-by-Step: How to Scale Autonomous Database
5. Monitoring & Life Cycle States
6. Elastic Pools and User Management (brief mention)
7. Summary

---

##  1. What is Oracle Autonomous Database Serverless?

Oracle Autonomous Database Serverless is a type of deployment on Oracle Cloud Infrastructure (OCI) where:

* You **don’t manage infrastructure** manually.
* The system handles **provisioning**, **patching**, **backup**, **scaling**, and **optimization** automatically.
* You only need to **specify your compute and storage** needs — the system handles the rest.

This makes it ideal for workloads like:

* OLTP (Autonomous Transaction Processing or ATP)
* Analytics (Autonomous Data Warehouse or ADW)
* Mixed Workloads

---

##  2. Key Features: Compute and Storage Scaling

### ➤ Independent Scaling

Autonomous Database allows you to scale:

* **ECPUs (Compute Units)** — for processing capacity
* **Storage** — for data storage needs

You can **scale compute and storage independently**, which means:

* You can increase CPU power without increasing storage
* Or, add more storage without changing compute power

This helps in **optimizing cost and performance** based on real workload patterns.

---

##  3. Understanding Auto Scaling

###  What is Auto Scaling?

Auto Scaling allows the database to **automatically increase compute capacity** in response to increased workload demands.

* **Auto Scaling Factor**: Up to **3×** the provisioned CPU count
* **Default**: Enabled by default (except for Always Free tier)
* **Dynamic**: Can be toggled **on/off without downtime**

> Example: If you provision 2 ECPUs, auto scaling can increase it up to 6 ECPUs when needed. If you manually set it to 6, auto scaling can go up to 18 ECPUs.

###  Note:

* Auto Scaling is **not available** in the **Always Free** tier.
* It is **enabled by default** in paid tiers.

---

##  4. Step-by-Step: Scaling the Autonomous Database

Let’s walk through how to **manually scale compute and storage** in the Autonomous Database:

###  Step 1: Navigate to Your Database

* Go to the **OCI Console**.
* Select the Autonomous Database you want to scale (e.g., **ATP Demo**).

###  Step 2: View Current Configuration

* On the **Database Console page**, you will see:

  * Current **ECPU count** (e.g., 2)
  * Current **Storage** (e.g., 1 TB)
  * **Auto Scaling** status (enabled or disabled)

###  Step 3: Manage Resource Allocation

* Click the **"Manage Resource Allocation"** button.
* A pop-up window will appear with:

  * Current ECPU and storage settings
  * **Toggle for Auto Scaling** (enabled by default)

You can:

* **Increase or decrease** the number of CPUs
* **Change storage** size
* **Enable/Disable** auto scaling

 **No downtime is required** for these changes.

###  Step 4: Observe Scaling Progress

* Once changes are applied:

  * Database status shows **“Scaling in Progress”**
  * Life cycle state reflects real-time updates
  * Database remains **available and operational** throughout

This means users and sessions can **continue working normally** while scaling occurs.

###  Step 5: Confirm Scaling Completion

* When scaling is complete:

  * Status changes to **“Available”**
  * New ECPU count is visible (e.g., increased from 2 → 6)
  * If auto scaling is enabled, the system can now scale up to 3× this value (i.e., 18 ECPUs)

---

##  5. Monitoring and Lifecycle States

### Life Cycle States You May See:

* **Available**: DB is ready and operational
* **Scaling in Progress**: CPU or storage changes are underway
* **Stopped/Terminated**: DB is not currently running (manual action)

Monitoring tools available:

* **OCI Metrics** (CPU, Storage, Sessions)
* **Alerts** for resource thresholds
* **REST APIs** for automation/integration

---

##  6. Elastic Pools and User Management (Brief Mention)

While not detailed in the demo, it's worth noting that:

* **Elastic pools** allow sharing compute across multiple autonomous databases, improving cost efficiency.
* **User management** can be handled via SQL Developer, SQL commands, or OCI Console.
* You can define roles, privileges, and connect via wallet or TCPS.

---

##  7. Summary

| Feature                 | Description                                         |
| ----------------------- | --------------------------------------------------- |
| **Independent Scaling** | Scale compute and storage separately                |
| **Auto Scaling**        | Scale up to 3× base CPUs automatically              |
| **Zero Downtime**       | All scaling operations happen while DB stays online |
| **Elastic Pools**       | Share compute resources across multiple databases   |
| **Monitoring**          | Real-time lifecycle status, resource metrics        |

---

##  Try It Yourself!

You can experiment with:

* **ATP or ADW workloads**
* Enable/disable auto scaling
* Monitor behavior under load
* Simulate performance scaling

---

