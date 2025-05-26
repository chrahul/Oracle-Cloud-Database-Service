**Maintenance Scheduling in Autonomous Database Dedicated (ADB-D)**

---

##  **Tutorial: Maintenance Scheduling in Autonomous Database Dedicated (ADB-D)**

---

###  **Overview**

Autonomous Database Dedicated (ADB-D) gives enterprise users granular control over maintenance operations, unlike the shared Autonomous Database model. This includes **custom scheduling of software updates, patching, and version control**, empowering organizations to independently validate and deploy updates across development, staging, and production environments.

This tutorial covers:

* The structure and flexibility of patching schedules
* How to configure patching preferences for various layers (Infrastructure, VM Cluster, ACD)
* Best practices for mission-critical workloads
* Manual patching and one-off patch handling
* Monitoring events and alerts for patching activities

---

###  **Why Custom Maintenance Scheduling Matters**

In large organizations, uncontrolled updates can break critical workloads. ADB-D solves this by allowing:

* Independent control over **when** and **where** updates happen
* Environment-specific patch levels (e.g., Dev always latest, Prod more conservative)
* Scheduling flexibility: patch **in a specific week, on a specific day, during a specific window**
* Auto-patching with **user-defined rules** and **“Patch Now”** override capability

---

###  **Autonomous Dedicated Stack: Maintenance Layers**

Maintenance can be scheduled **independently** across three logical components:

1. **Exadata Infrastructure** (physical layer)
2. **Autonomous VM Cluster (AVMC)** (compute layer)
3. **Autonomous Container Database (ACD)** (database management layer)

Each component can have:

* Different **update schedules**
* Different **software versions**
* Separate **policies for skipping or applying patches**

---

### 🕓 **How to Configure Maintenance Schedule**

In the OCI Console or via CLI/API:

#### Step 1: Go to the ADB-D resource (Infrastructure / AVMC / ACD)

#### Step 2: Click on **Maintenance Settings**

#### Step 3: Choose:

* **Quarter** (e.g., Q1, Q2, Q3, Q4)
* **Month in Quarter** (e.g., March)
* **Week in Month** (e.g., 2nd week)
* **Day in Week** (e.g., Wednesday)
* **Maintenance Window** (e.g., 2AM–6AM UTC)

#### Step 4: Confirm or modify schedule dynamically

You can also reschedule or initiate patching manually anytime using:

* **“Patch Now”** option
* **CLI/REST API**
* **OCI SDKs (Java, Python, Go, Node.js)**

---

###  **Built-in Best Practices**

Oracle recommends and enables:

* **Staggered Environments**:

  * Dev: Always patched to the latest
  * Staging: Validated version from Dev
  * Prod: Alternate quarter’s release or after full validation

* **Patch Skipping**: Skip one quarter and move to the next

* **Mission-Critical Database Isolation**: Use a different schedule for ADBs that cannot afford downtime

---

###  **One-Off Patching**

Not all patches are part of the scheduled cycle.

* For critical issues, Oracle supports **one-off patches** initiated manually
* These can be **scheduled or run immediately**
* Typically used for **urgent security fixes or known issue resolution**

---

###  **Maintenance Events and Notifications**

OCI automatically publishes:

* **Quarterly Update Announcements**
* **Maintenance Reminders**
* **Maintenance Begin/End Events**

Notifications are sent via:

* **OCI Console**
* **Event Service + Notifications**
* **Email / PagerDuty / Slack integrations**

> You can subscribe to these events in the OCI Console > Event Rules > Notifications.

---

### 🔧 **Maintenance Operation Methods**

Maintenance actions can be triggered through:

*  OCI Console
*  OCI CLI (`oci db autonomous-database patch`)
*  REST APIs
*  SDKs (Java, Python, Go, etc.)

---

###  **Fleet Administrator's Advantage**

Fleet Admins can:

* Maintain **different patch levels** for environments
* Set and enforce **governed maintenance windows**
* Ensure mission-critical apps are patched only after extensive testing
* Maintain **long-term version consistency** across workloads

---

###  **References & Further Reading**

Refer to Oracle’s official documentation for deeper exploration:

* [Autonomous Database Dedicated Maintenance Scheduling](https://docs.oracle.com/en/cloud/paas/autonomous-database-dedicated/)
* [OCI Events and Notifications](https://docs.oracle.com/en-us/iaas/Content/Events/home.htm)
* [OCI Maintenance and Patching APIs](https://docs.oracle.com/en-us/iaas/api/)
* [Autonomous Database CLI Command Reference](https://docs.oracle.com/en-us/iaas/tools/oci-cli/latest/oci_cli_docs/cmdref/db/autonomous-database/index.html)

---

###  **Conclusion**

Autonomous Dedicated offers unmatched control and visibility over patching and maintenance, aligning with enterprise IT governance. By leveraging OCI’s native scheduling capabilities, customers can reduce downtime risk, ensure compliance, and maintain application continuity — all while using Oracle-managed infrastructure.

---


