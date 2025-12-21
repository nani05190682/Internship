
# 🔐 Lab Exercise: Symmetric Key Encryption on Linux (Using OpenSSL & GPG)

## 🎯 Lab Objective

By the end of this lab, the learner will be able to:

* Understand **symmetric key encryption**
* Encrypt and decrypt files using:

  * **OpenSSL (AES)**
  * **GPG symmetric encryption**
* Verify encryption and integrity
* Understand real-time Linux use cases

---

## 🧠 Theory (Quick Overview)

**Symmetric Key Encryption** uses:

* **One shared secret key**
* Same key for **encryption & decryption**
* Faster than asymmetric encryption
* Common algorithms: **AES, DES, Blowfish**

📌 Real-time usage:

* File encryption
* Database backups
* Secure configuration files
* Password vaults

---

## 🧪 Lab Environment

* OS: **RHEL / CentOS / Ubuntu**
* User: Non-root or root
* Packages:

  * `openssl`
  * `gnupg`

---

## 🔹 Task 1: Create a Sample File

```bash
mkdir ~/crypto-lab
cd ~/crypto-lab
```

```bash
echo "This is confidential salary data" > secret.txt
```

Verify:

```bash
cat secret.txt
```

---

## 🔹 Task 2: Encrypt File Using OpenSSL (AES-256)

### 🔐 Encryption

```bash
openssl enc -aes-256-cbc -salt -in secret.txt -out secret.txt.enc
```

✔ Enter a password when prompted.

Verify:

```bash
ls -l
```

Try reading encrypted file:

```bash
cat secret.txt.enc
```

📌 Output should be unreadable (binary data).

---

## 🔹 Task 3: Decrypt the File Using OpenSSL

```bash
openssl enc -aes-256-cbc -d -in secret.txt.enc -out secret_decrypted.txt
```

Verify:

```bash
cat secret_decrypted.txt
```

✅ Content should match original file.

---

## 🔹 Task 4: Verify File Integrity (Optional but Recommended)

```bash
sha256sum secret.txt secret_decrypted.txt
```

✔ Both hashes should match.

---

## 🔹 Task 5: Encrypt Using GPG (Symmetric Mode)

### 🔐 Encryption

```bash
gpg --symmetric secret.txt
```

Enter passphrase.

Verify:

```bash
ls
```

Output:

```
secret.txt.gpg
```

---

## 🔹 Task 6: Decrypt GPG Encrypted File

```bash
gpg --output secret_gpg_decrypted.txt --decrypt secret.txt.gpg
```

Verify:

```bash
cat secret_gpg_decrypted.txt
```

---

## 🔹 Task 7: Compare OpenSSL vs GPG

| Feature         | OpenSSL             | GPG                 |
| --------------- | ------------------- | ------------------- |
| Ease of use     | Medium              | Easy                |
| Integrity check | Manual              | Built-in            |
| Password based  | Yes                 | Yes                 |
| Common usage    | Automation, scripts | Secure file sharing |

---

## 🔹 Task 8: Real-Time Scenario

### 📌 Scenario:

Encrypt a configuration file before uploading it to GitHub.

```bash
openssl enc -aes-256-cbc -salt -in app.conf -out app.conf.enc
```

Decrypt during deployment:

```bash
openssl enc -aes-256-cbc -d -in app.conf.enc -out app.conf
```

---



