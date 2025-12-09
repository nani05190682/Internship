Hands-On Lab: Hardening Kali Linux


These steps are continued from the previous page.

---

## Task 6: Manage User Groups

Instead of setting permissions for each user one at a time, you can add users to groups appropriate for their roles. In Linux, a group is a collection of users, and you can set permissions for the entire group.

**Example:** Assume that your HR department has numerous employees, each needing access to the HR directory and several other directories. You could:

* Create a group named `hr`.
* Grant this group access to the appropriate directories.
* Add all HR employees’ user accounts to the `hr` group.

This ensures that employees in the same role have the same level of access.

### Manage User Groups Using the Command Line

1. Create a new group:

   ```bash
   sudo groupadd testusers

The groupadd command adds a new group named testusers.

Add a user to the group:

sudo usermod -a -G testusers test

usermod modifies an existing user.

-a appends the user to the group without removing them from others.

-G specifies the group(s) to add the user to.

Confirm the user was added:

getent group

Each line shows:

Group name (e.g., adm).

Encrypted password placeholder (x).

Group ID (GID).

Users in the group.

Scroll to find testusers with user test listed.

Task 6: Manage User Groups

Instead of setting permissions for each user one at a time, you can add users to groups appropriate for their roles. In Linux, a group is a collection of users, and you can set permissions for the entire group.

Example: Assume that your HR department has numerous employees, each needing access to the HR directory and several other directories. You could:

Create a group named hr.

Grant this group access to the appropriate directories.

Add all HR employees’ user accounts to the hr group.

This ensures that employees in the same role have the same level of access.

Manage User Groups Using the Command Line

Create a new group:

sudo groupadd testusers

The groupadd command adds a new group named testusers.

Add a user to the group:

sudo usermod -a -G testusers test

usermod modifies an existing user.

-a appends the user to the group without removing them from others.

-G specifies the group(s) to add the user to.

Confirm the user was added:

getent group

Each line shows:

Group name (e.g., adm).

Encrypted password placeholder (x).

Group ID (GID).

Users in the group.

Scroll to find testusers with user test listed.

Manage User Groups Using the GUI

Navigate: Applications > Usual Applications > System > Users and Groups.

Select Test Two from the list of users, then click Manage Groups.

In the Groups settings window, click Add to create a new group if needed.

Select testusers and click Properties.

Confirm user test is listed with a checkmark. Note the GID (e.g., 1002).

Add user TestTwo by selecting the checkbox and clicking OK.

Confirm both test and TestTwo are listed in the group.

Close the settings windows.

Task 7: Configure the Firewall Using UFW

A firewall controls traffic to and from a network or device using rules you specify. In this lab, you’ll install and configure Uncomplicated Firewall (ufw).

Steps

Install ufw:

sudo apt install ufw

Check firewall status:

sudo ufw status

Initially inactive.

Enable the firewall:

sudo ufw enable

Confirm status:

sudo ufw status

View detailed status:

sudo ufw status verbose

Default rules:

Deny all incoming traffic.

Allow all outgoing traffic.

Disable routed traffic.

Allow SSH (port 22):

sudo ufw allow 22/tcp

Allow HTTP (port 80):

sudo ufw allow 80/tcp

Deny Telnet (port 23):

sudo ufw deny 23

Confirm rules:

sudo ufw status verbose

Rules apply to both IPv4 and IPv6.

Disable the firewall (for demonstration only):

sudo ufw disable

Note: In a real environment, always enable the firewall with rules tailored to your organization’s needs.
