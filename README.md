# 🚀 Ansible Automation

Ansible is a powerful open-source automation tool used for configuration management, application deployment, and task automation. It is agentless, relying on SSH to communicate with remote nodes, and uses simple YAML-based playbooks to define automation tasks.

---

## 🧠 Why Use Ansible?

- ✅ **Agentless** – No need to install agents on managed nodes.
- ✅ **Simple** – Playbooks are written in YAML, which is human-readable.
- ✅ **Idempotent** – Ensures tasks run only if required.
- ✅ **Powerful** – Supports variables, conditionals, handlers, and roles.
- ✅ **Extensible** – Easily integrates with cloud platforms, CI/CD, and other tools.

---

![Ansible Workflow](https://www.tutorialspoint.com/ansible/images/ansible_works.jpg)

---

## 📂 Inventory Configuration

Update your inventory file:
```ini
[web]
192.168.1.101 ansible_user=ansible

[db]
192.168.1.102 ansible_user=ansible

# Ungrouped Host (doesn't belong to any group)
192.168.1.200 ansible_user=ansible
```

Define variables in:
- `group_vars/all.yml`
- `host_vars/<hostname>.yml`

---

## 📜 Running Playbooks

```bash
# It will check the syntax of a playbook
ansible-playbook <playbook-yml-file> --syntax-check

# It will display which hosts would be affected by a playbook before run
ansible-playbook <playbook-yml-file> --list-hosts

# Run the playbook using below command
ansible-playbook <playbook-yml-file>

# It executes one-step-at-a-time, confirm each task before running
ansible-playbook <playbook-yml-file> --step

# Run the playbook in verbose mode
ansible-playbook <playbook-yml-file> -vvv
```

---

## 🔐 Using Ansible Vault

Ansible Vault
===============

=> It is used to secure our playbooks

=> Using Ansible vault concept, we can encrypt & decrypt our playbooks	

  - **Encryption**: Convert data from readable format to un-readable format  
  - **Decryption**: Convert data from un-readable format to readable format

```bash
# Create a new encrypted file
ansible-vault create vault/secrets.yml

# Encrypt an existing file
ansible-vault encrypt <yml-file-name>

# See encrypted content (raw)
cat <yml-file-name>

# View decrypted content without editing
ansible-vault view <yml-file-name>

# Edit the encrypted file
ansible-vault edit <yml-file-name>

# Run an encrypted playbook
ansible-playbook <yml-file-name> --ask-vault-pass

# Decrypt the playbook
ansible-vault decrypt <yml-file-name>
```

# 🚀 Ansible Automation

![Deployed using Ansible by Sudarshan Gawande](https://github.com/sudarshan-gawande/extra-images/blob/main/ansible-deployment.png)

Ansible is a powerful open-source automation tool used for configuration management, application deployment, and task automation...

---

## 📄 License

Licensed under the [MIT License](LICENSE)

---

## 📧 Contact  
📧 **Email**: [sudarshangawande98@gmail.com](mailto:sudarshangawande98@gmail.com)  
🔗 **GitHub**: [Sudarshan Gawande](https://github.com/sudarshan-gawande)  
🌐 **Portfolio**: [sudarshangawande.com](https://sudarshangawande.com)  
💼 **LinkedIn**: [Sudarshan Gawande](https://www.linkedin.com/in/sudarshan-gawande/)  

