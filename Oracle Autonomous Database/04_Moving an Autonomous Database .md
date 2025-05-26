**move an Oracle Autonomous Database to a different compartment**

---

##  Moving an Autonomous Database to a Different Compartment in OCI

### 🧾 Business Reasons for Moving

* To **align with organizational structure** (e.g., Dev, Test, Prod environments).
* To place the database in a **compartment with appropriate network resources** (e.g., a different subnet or VCN).
* To **leverage access policies** already defined in another compartment.
* For **project or cost-center reallocation**.

---

###  What Gets Moved?

| Resource                         | Moves With It?                                     |
| -------------------------------- | -------------------------------------------------- |
| Autonomous Database              | ✅ Yes                                              |
| Automatic Backups                | ✅ Yes                                              |
| Metadata and Configuration       | ✅ Yes                                              |
| Network Setup (e.g., Subnet/VCN) | ❌ No (must remain same unless DB is reprovisioned) |

---

###  Prerequisites

| Requirement                 | Details                                                                                                                                                                                                                 |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|  **IAM Permissions**      | You must have proper permissions in **both** source and target compartments. Specifically: <br> - `DATABASE_MANAGE` permission for Autonomous Databases. <br> - `inspect`, `move`, or `update` actions on the resource. |
|  **Compartment Policies** | Once moved, the **target compartment's policies** are applied immediately to the database.                                                                                                                              |
|  **Compartment Limits**   | Ensure the target compartment has **no quota limits** blocking new database resources.                                                                                                                                  |

---

###  How to Move (Using OCI Console)

1. **Go to**: Autonomous Databases page in OCI Console.
2. **Locate** your database (e.g., `ATP Demo`) in the current compartment.
3. **Click the Actions Menu** (⋮) → Select **Move Resource**.
4. **Choose Target Compartment** from the dropdown list.
5. **Confirm** the operation.
6. **Monitor** the progress via the **Work Requests** page.
7.  Once complete, the DB will appear under the **new compartment**, and backups are migrated as well.

---

###  Key Notes

*  The move operation is **non-disruptive**—no DB downtime.
*  IAM **authorization and access** may change based on policies in the target compartment.
*  You **cannot move** a DB across tenancies (only within the same tenancy).
*  **Tags and billing** may reflect the new compartment post-move.

---

###  Summary

| Feature                           | Supports                             |
| --------------------------------- | ------------------------------------ |
| **Easy one-click move**           |  Yes                                |
| **Automatic backup migration**    |  Yes                                |
| **IAM Policy auto-update**        |  Applies target compartment's rules |
| **Network change (e.g., Subnet)** |  Not part of move                   |
| **Cross-tenancy move**            |  Not allowed                        |

---

