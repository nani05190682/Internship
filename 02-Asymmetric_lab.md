

# 🔐 Lab Exercise: Asymmetric Key Encryption on Linux (Using GPG & OpenSSL)

## 🎯 Lab Objective

By the end of this lab, the learner will be able to:

* Understand **asymmetric (public-key) encryption**
* Generate **public and private keys**
* Encrypt data using a **public key**
* Decrypt data using a **private key**
* Understand real-world Linux use cases

---

## 🧠 Theory (Quick Overview)

**Asymmetric Encryption** uses:

* **Two keys**

  * 🔑 Public Key → Encryption
  * 🔐 Private Key → Decryption
* More secure for **key exchange**
* Slower than symmetric encryption

📌 Common algorithms:

* **RSA**
* **ECC**
* **DSA**

📌 Real-world usage:

* SSH login
* HTTPS (TLS)
* Secure email
* Key exchange in cloud & DevOps

---

## 🧪 Lab Environment

* OS: RHEL / CentOS / Ubuntu
* Packages:

  * `gnupg`
  * `openssl`
* User: Normal user

---

# 🔹 PART 1: Asymmetric Encryption Using GPG (Recommended)

---

## 🔹 Task 1: Create Lab Directory & Sample File

```bash
mkdir ~/asymmetric-lab
cd ~/asymmetric-lab
```

```bash
echo "This is confidential project data" > message.txt
```

Verify:

```bash
cat message.txt
```

---

## 🔹 Task 2: Generate GPG Key Pair

```bash
gpg --full-generate-key
```

Choose:

* Key type: **RSA and RSA**
* Key size: **2048 or 4096**
* Expiry: 1 year
* Name: `Linux User`
* Email: `linuxuser@example.com`
* Passphrase: Strong password

Verify keys:

```bash
gpg --list-keys
gpg --list-secret-keys
```

---

## 🔹 Task 3: Export Public Key (Shareable)

```bash
gpg --export -a linuxuser@example.com > public.key
```

View:

```bash
cat public.key
```

📌 Public key can be shared safely.

---

## 🔹 Task 4: Encrypt File Using Public Key

```bash
gpg --encrypt --recipient linuxuser@example.com message.txt
```

Verify:

```bash
ls
```

Output:

```
message.txt.gpg
```

Try to view:

```bash
cat message.txt.gpg
```

👉 Encrypted binary data

---

## 🔹 Task 5: Decrypt Using Private Key

```bash
gpg --decrypt message.txt.gpg
```

OR save output:

```bash
gpg --output message_decrypted.txt --decrypt message.txt.gpg
```

Verify:

```bash
cat message_decrypted.txt
```

---

## 🔹 Task 6: Simulate Real-World Scenario (Two Users)

### Export public key:

```bash
gpg --export -a linuxuser@example.com > linuxuser_pub.key
```

### Import on another system/user:

```bash
gpg --import linuxuser_pub.key
```

Encrypt using imported public key:

```bash
gpg --encrypt --recipient linuxuser@example.com secret.txt
```

📌 Only the **private key holder** can decrypt.

---

# 🔹 PART 2: Asymmetric Encryption Using OpenSSL (RSA)

---

## 🔹 Task 7: Generate RSA Private Key

```bash
openssl genrsa -out private.key 2048
```

Verify:

```bash
ls -l private.key
```

---

## 🔹 Task 8: Extract Public Key

```bash
openssl rsa -in private.key -pubout -out public.key
```

View:

```bash
cat public.key
```

---

## 🔹 Task 9: Encrypt Using Public Key

```bash
openssl rsautl -encrypt -inkey public.key -pubin -in message.txt -out message.enc
```

---

## 🔹 Task 10: Decrypt Using Private Key

```bash
openssl rsautl -decrypt -inkey private.key -in message.enc -out message_dec.txt
```

Verify:

```bash
cat message_dec.txt
```

---

## 🔹 Task 11: Compare GPG vs OpenSSL

| Feature          | GPG      | OpenSSL |
| ---------------- | -------- | ------- |
| Ease of use      | Easy     | Medium  |
| Key management   | Built-in | Manual  |
| Email encryption | Yes      | No      |
| Automation       | Moderate | High    |

---

## 📌 Lab Completion Checklist

✅ Key pair generated
✅ Public key shared
✅ File encrypted with public key
✅ File decrypted with private key

---

