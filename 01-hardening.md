
---

# **Task : Manage User Groups**

Managing individual permissions for each user can be time-consuming. Instead, Linux allows you to group users based on their department or role. Permissions can then be applied to the entire group at once.

### **Real-Time Example**

Suppose your **HR department** has many employees who all need access to the `/hr` directory and some other restricted folders. Instead of configuring each user individually, you can:

* Create a group named **hr**
* Assign permissions for `/hr` to the **hr** group
* Add all HR employee accounts to the **hr** group

This ensures **consistent, role-based access control**.

---

## **Manage User Groups Using the Command Line**

### **1. Create a New Group**

```bash
sudo groupadd testusers
```

**Explanation:**

* `groupadd` creates a new group named **testusers**.

---

### **2. Add a User to the Group**

```bash
sudo usermod -a -G testusers test
```

**Explanation:**

* `usermod` modifies an existing user
* `-a` → *append*, ensures the user is added without removing them from other groups
* `-G` → specifies the group(s) to add the user to

---

### **3. Confirm the User Was Added**

```bash
getent group
```

Each line displays:

* **Group name** (example: `adm`)
* **Password placeholder** (`x`)
* **Group ID** (GID)
* **Users in that group**

Scroll until you find:

```
testusers:x:<GID>:test
```

This confirms that **test** is now part of the `testusers` group.

---

## **Manage User Groups Using the GUI (Graphical Interface)**

1. Navigate to:
   **Applications → Usual Applications → System → Users and Groups**
2. Select **Test Two** from the list of users
3. Click **Manage Groups**
4. In the Groups window, you may click **Add** to create a new group if needed
5. Select **testusers**, then click **Properties**
6. Confirm that user **test** is listed and checked

   * Note: The GID may appear here (e.g., **1002**)
7. To add another user, check **TestTwo** and click **OK**
8. Ensure both **test** and **TestTwo** appear as members of the group
9. Close all settings windows

---

# **Task 7: Configure the Firewall Using UFW**

A **firewall** filters network traffic based on rules you define.
In this task, you will install and configure **UFW (Uncomplicated Firewall)**, a simple yet powerful firewall tool for Ubuntu/Debian systems.

---

## **Steps to Configure UFW**

### **1. Install UFW**

```bash
sudo apt install ufw
```

---

### **2. Check Firewall Status**

```bash
sudo ufw status
```

Initially, it will show:

```
Status: inactive
```

---

### **3. Enable the Firewall**

```bash
sudo ufw enable
```

---

### **4. Verify Status**

```bash
sudo ufw status
```

Check detailed status:

```bash
sudo ufw status verbose
```

Default rules:

* Deny **all incoming** traffic
* Allow **all outgoing** traffic
* Routed traffic disabled

---

## **5. Add Firewall Rules**

### **Allow SSH (Port 22)**

```bash
sudo ufw allow 22/tcp
```

### **Allow HTTP (Port 80)**

```bash
sudo ufw allow 80/tcp
```

### **Deny Telnet (Port 23)**

```bash
sudo ufw deny 23
```

---

### **6. Review Rules**

```bash
sudo ufw status verbose
```

You will see rules applied for both **IPv4** and **IPv6**.

---

### **7. Disable the Firewall (Demo Only)**

```bash
sudo ufw disable
```

> **Important:**
> In real production environments, always keep the firewall enabled and properly configured based on your organization’s security policies.

---
