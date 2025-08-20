
<h1 = align=center>𝙷𝙾𝙼𝙴 𝙻𝙰𝙱 - SOCIAL ENGINEERING TOOLKIT (SET)</h1>

<p align="center">
<img width="1342" height="883" alt="Untitled Diagram drawio (3)" src="https://ars.els-cdn.com/content/image/3-s2.0-B9780128021491000087-f08-04-9780128021491.jpg" />
</p>

## 📌 Introduction

Social engineering is the use of deception and manipulation to gain access to information or resources. Rather than exploiting technical vulnerabilities, attackers target human weaknesses to extract sensitive data such as usernames and passwords.

This lab simulates a real-world phishing attack using command-line tools and demonstrates how attackers can execute such strategies using the **Social Engineer Toolkit (SET)**.

## 🛠️ TECHNOLOGY & TOOLS UTILIZED
- **`VirtualBox:`**  
  Used as the primary virtualization platform to host multiple virtual machines in an isolated local environment for cybersecurity testing and infrastructure simulation.

- **`Social-Engineer Toolkit (SET)`**  
 Used to execute system commands, run the SET toolkit, and control services like Apache. Essential for interacting with the system in a controlled, scriptable way.

- **`Linux Terminal (Bash Shell)`**  
  Installed as a domain-joined workstation to simulate a typical enterprise endpoint. Used for user behavior simulation, GPO testing, and endpoint visibility through logging tools.

- **`Active Directory:`**  
  Implemented to manage user accounts, groups, and organizational units (OUs). Used for hands-on experience with authentication flows, access control, privilege escalation testing, and administrative scripting.

- **`Web Browser:`**  
 Used by the simulated victim to visit the cloned phishing website and enter login credentials.
  
- **`Local Network (LAN):`**  
  The phishing server is hosted on a local IP (e.g., 192.168.x.x) that is accessed by the simulated victim machine via a browser.

 ## OBJECTIVE

The objective of this lab is to simulate a realistic phishing attack using social engineering techniques in a safe, virtualized environment. By leveraging the Social-Engineer Toolkit (SET) and command-line tools, students will gain hands-on experience in understanding how attackers exploit human behavior to compromise system security.

Specifically, this lab aims to:

- Introduce the core principles of **social engineering** and its relevance in cybersecurity.
- Demonstrate how to **plan and execute a phishing attack** using Terminal-based tools.
- Simulate the **harvesting of user credentials** through a cloned website hosted locally.
- Reinforce awareness of how easily end-users can be deceived by **legitimate-looking attack vectors**.
- Emphasize the importance of **defensive countermeasures**, such as user training and technical safeguards.

> 🔐 This lab is conducted in a **controlled environment** and is intended **solely for educational purposes**.

## STEP 1 :  Stopping the Apache HTTP Server

After logging into the environment, before launching the phishing simulation, you need to stop any web services currently running on `port 80 (commonly Apache)`.
**Steps:**

1. Launch a Terminal window.
2. Run the following command: `service apache2 stop`

   <img width="1131" height="471" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/stop_appache.png" /></br>

(🔐 This ensures the Social Engineer Toolkit can use port 80 without conflict.)

## STEP 2 : Setting Up the Phishing Page

1. Open a second Terminal window.
2. Launch `SET`:
```bash
sudo setoolkit
```
 <img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20184737.png" /></br>

3. From the menu, select the following options:

<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/options.png" /></br>
<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20185333.png" /></br>
<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20185638.png" /></br>
<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20185838.png" /></br>

4. Switch back to the first Terminal window and execute the following command to observe the IP address of the eth0 ethernet:

```bash
ifconfig eth0
```
 
5. Switch back to the second Terminal window, type the IP adddress and press Enter:
   
<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20190258.png" /></br>

6. When asked `Select a template`, type 2, and press Enter:

<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20190628.png" /></br>

7. When asked Press (return) if you understand what we're saying here, press Enter.

## STEP 3 : TRACKING / HUNTING Victims

Open the browser window and access the Google accounts with the IP address found earlier from `STEP 2`. Sign in with an email and password that was created. Restore the second Terminal window and verify that the entered email and password visible on the screen

1. From the left sidebar, click the Firefox ESRicon
2.  In the address bar, type: `http://<ip address>` and press Enter. (Replace `<ip address>` with the IP address obtained from earlier of the lab.
3.  In the Sign In - Google Accounts window, type Email and Password information. (in this lab, it was created as email: john12@gmail.com and password: john123456) and then press Enter or click Sign in
 

<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20191509.png" /></br>

4. When the Would you like Firefox to remember this login? prompt ppears click teh close icon. you will observe hte Google page. After that, minimize FireFox ESR.

<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20191735.png" /></br>

5. In the second terminal window, you will observe the number of exploits. you will also observe the email and password that you entered in Step 3.

<img width="616" height="437" alt="Lab 4" src="https://raw.githubusercontent.com/DanielTsang26/SET/refs/heads/main/Screenshot%202025-08-19%20192024.png" /></br>

6. To stop all attacks: `Ctrl + C`


---
*This hands-on exercise provided a practical understanding of social engineering and how such attacks can be executed using tools like the **Social-Engineer Toolkit (SET)**.*

### 🔑 Key Takeaways

- 🧠 **Social engineering targets human vulnerabilities** rather than technical flaws.
- 🛠️ The **Social-Engineer Toolkit (SET)** allows for realistic simulation of phishing sites.
- 📥 **Credential harvesting through cloned sites** shows how easily users can be deceived.
- 🛡️ **Defensive strategies** such as user education, browser security, and network monitoring are critical to mitigating these types of attacks.

