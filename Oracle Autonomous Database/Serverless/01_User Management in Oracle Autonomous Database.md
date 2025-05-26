**User Management in Oracle Autonomous Database**

---

## User Management in Oracle Autonomous Database

### Admin User: Pre-Created

When you first provision an Autonomous Database, the `ADMIN` user is automatically created. You set the `ADMIN` password during provisioning. This user has full privileges and is used for all initial setup tasks.

---

### Creating Additional Users

You can create additional users either for:

* Application access, or
* Individual developers, analysts, and end users.

**Key Points:**

* No need to specify default or temporary tablespaces.
* Simplified user setup using roles such as `DWROLE`.

####  Steps to Create a User (Using SQL):

```sql
CREATE USER username IDENTIFIED BY "YourPassword1!";
GRANT DWROLE TO username;
```

* Password must meet [Oracle's complexity rules](https://docs.oracle.com/en/).
* `DWROLE` grants essential privileges for developers and analysts.

---

###  Methods to Create Users

1. **SQL Client Tools** (e.g., SQL Developer, SQL\*Plus)
2. **Oracle Database Actions (Web Console):**

   * Click **Database Actions** from the ADB overview page.
   * Go to **Administration > Database Users**.
   * Click **Create User**.
   * Provide username, password (and confirm).
   * Optionally enable: Graph, OML, or Web Access.
   * Click **Create User**.

---

###  Managing Roles and Permissions

* From the **Database Users** page:

  * Click **Edit** on the desired user card.
  * Go to **Granted Roles**.
  * Select:

    * `Granted` – to assign the role.
    * `Admin` – to allow the user to grant this role to others.
    * `Default` – if you want the role enabled by default.
  * Example roles:

    * `DWROLE` – for development and analysis.
    * `DATA_TRANSFORMS_USER` – for Data Transforms tool access.
  * Click **Apply Changes** to save.

---

###  Changing the Admin Password

You can reset the `ADMIN` password from:

* **Cloud Console:**

  * Click **More Actions > Reset Password** from the ADB details page.
  * Enter and confirm the new password.
* **SQL Client Tools:**

  ```sql
  ALTER USER ADMIN IDENTIFIED BY "NewSecurePassword1!";
  ```

---

###  Summary

You now know how to:

* Create and manage users in an Autonomous Database.
* Grant and revoke roles using GUI or SQL.
* Change the admin password securely.

This streamlined user management ensures secure, role-based access control and supports both GUI and script-driven workflows.


