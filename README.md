📝 Jenkins Installation on WSL (Ubuntu)
This guide provides step-by-step instructions for installing Jenkins on Windows Subsystem for Linux (WSL) using Ubuntu.

📌 Prerequisites
WSL installed and set to Ubuntu (WSL2 recommended).

Internet access.

Basic Linux command-line knowledge.

Administrator access in WSL.

🛠️ Step 1: Update System Packages
bash
Copy
Edit
''''
sudo apt update && sudo apt upgrade -y
''''
This updates your system's package index and upgrades all installed packages.

☕ Step 2: Install Java (Jenkins Dependency)
bash
Copy
Edit
sudo apt install openjdk-17-jdk -y
Jenkins requires Java to run. We use OpenJDK 17 here, which is a stable LTS version.

Verify installation:

bash
Copy
Edit
java -version
🔐 Step 3: Add Jenkins Repository and Key
Add the Jenkins Debian package repository and its GPG key:

bash
Copy
Edit
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
bash
Copy
Edit
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
📦 Step 4: Install Jenkins
bash
Copy
Edit
sudo apt update
sudo apt install jenkins -y
This will install the Jenkins server and its dependencies.

▶️ Step 5: Start Jenkins Service
Start Jenkins and ensure it's running:

bash
Copy
Edit
sudo service jenkins start
Check status:

bash
Copy
Edit
sudo service jenkins status
🌐 Step 6: Access Jenkins from Your Browser
📍 Option A: Using WSL IP Address
Find WSL's IP address:

bash
Copy
Edit
hostname -I
Open in Windows browser:

cpp
Copy
Edit
http://<WSL_IP>:8080
Replace <WSL_IP> with the actual IP from the previous command.

🔑 Step 7: Unlock Jenkins
Get the initial admin password:

bash
Copy
Edit
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Paste it into the Jenkins setup screen in the browser.

🧱 Step 8: Finish Setup
Install suggested plugins.

Create your first admin user.

Jenkins is ready to use.

🧠 Notes
By default, Jenkins runs on port 8080.

If localhost:8080 doesn't work, use the WSL IP address.

For persistent access, consider setting up a reverse proxy with Nginx.

