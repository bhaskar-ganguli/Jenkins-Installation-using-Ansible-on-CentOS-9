# 🚀 Jenkins Installation using Ansible on CentOS 9

This project automates the installation and configuration of Jenkins on a CentOS 9 managed node using Ansible.

---

## 📌 Project Overview

This Ansible playbook performs the following tasks:

* Installs required dependencies (Java, wget, curl)
* Adds Jenkins repository and imports GPG key
* Installs and starts Jenkins service
* Configures firewall to allow port 8080
* Waits for Jenkins service to become available
* Retrieves and displays the initial admin password

---

## 🏗️ Architecture

* **Control Node**: Machine where Ansible is installed
* **Managed Node (node1)**: CentOS 9 server where Jenkins is deployed

---

## 📂 Project Structure

```
jenkins-ansible-setup/
│
├── inventories/
│   └── hosts.ini
│
├── playbooks/
│   └── install_jenkins.yml
│
├── group_vars/
│   └── all.yml
│
├── ansible.cfg
├── README.md
└── .gitignore
```

---

## ⚙️ Prerequisites

Before running this project, ensure:

* Ansible is installed on the control node
* SSH access is configured between control and managed node
* Managed node is running CentOS 9
* Port **8080** is open:

  * OS firewall (firewalld)
  * Cloud firewall (GCP / AWS / Azure)

---

## ▶️ How to Run the Playbook

1. Clone the repository:

```bash
git clone https://github.com/your-username/jenkins-ansible-setup.git
cd jenkins-ansible-setup
```

2. Update inventory file:

```
inventories/hosts.ini
```

Example:

```
[node1]
<your-server-ip> ansible_user=centos ansible_ssh_private_key_file=~/.ssh/id_rsa
```

3. Run the playbook:

```bash
ansible-playbook playbooks/install_jenkins.yml
```

---

## 🌐 Access Jenkins

After successful execution, open your browser:

```
http://<your-server-ip>:8080
```

---

## 🔑 Initial Admin Password

The playbook automatically retrieves and displays the Jenkins initial admin password.

You can also manually fetch it:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

## ⚠️ Notes

* The Jenkins UI may show **"Not Secure"** since it uses HTTP by default
* For production environments, configure:

  * Reverse proxy (Nginx)
  * SSL/HTTPS

---

## 🚀 Future Improvements

You can enhance this project by adding:

* 🔐 HTTPS using Nginx + SSL
* 👤 Automated admin user creation
* 📦 Jenkins plugin installation via Ansible
* 🐳 Containerized Jenkins using Docker
* ☁️ Infrastructure provisioning using Terraform

---

## 🤝 Contributing

Feel free to fork this repository and improve it. Pull requests are welcome!

---

## 📄 License

This project is open-source and available under the MIT License.
