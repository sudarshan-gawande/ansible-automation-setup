# 🧾 Ansible Command Cheat Sheet

---

## 🧠 Ansible Ad-Hoc Commands

Ad-hoc commands are one-liner shell-style commands used to perform tasks quickly without writing a playbook.

**Syntax:**
```bash
ansible [all/group-name/host] -m <module> -a <args>
```

**Examples:**
```bash
ansible all -m ping
ansible webservers -m ping
ansible dbservers -m ping
ansible all -m shell -a "date"
ansible all -m yum -a "name=git"
ansible webservers -m yum -a "name=httpd"
```

### Commonly Used Modules:
- `ping` – Check connectivity
- `shell` – Run shell commands
- `yum` / `apt` – Install packages
- `service` – Manage services
- `copy` – Copy files to hosts

---

## 📜 Playbook Commands

```bash
# Check syntax of a playbook
ansible-playbook <playbook-yml-file> --syntax-check

# List affected hosts before executing
ansible-playbook <playbook-yml-file> --list-hosts

# Run a playbook
ansible-playbook <playbook-yml-file>

# Step-by-step execution
ansible-playbook <playbook-yml-file> --step

# Run in verbose mode
ansible-playbook <playbook-yml-file> -vvv

# Execute a specific tag
ansible-playbook handlers_tags.yml --tags "install"

# Execute multiple tags
ansible-playbook handlers_tags.yml --tags "install,copy"

# Skip specific tags
ansible-playbook handlers_tags.yml --skip-tags "install,copy"

# Run with extra variables
ansible-playbook <playbook-yml-file> --extra-vars "package_name=httpd"
```

---

## 🔐 Ansible Vault Commands

```bash
# Encrypt a file (e.g. secrets, playbook)
ansible-vault encrypt <yml-file-name>

# View encrypted file (as raw)
cat <yml-file-name>

# View decrypted content
ansible-vault view <yml-file-name>

# Edit encrypted file
ansible-vault edit <yml-file-name>

# Run encrypted playbook
ansible-playbook <yml-file-name> --ask-vault-pass

# Decrypt the file
ansible-vault decrypt <yml-file-name>
```

Note: Vault encryption requires setting a vault password.

---

## 📦 Role Commands

```bash
# Initialize a new role
ansible-galaxy init <role-name>

# Install roles from requirements.yml
ansible-galaxy install -r requirements.yml
```

---

## 🧪 Linting & Validation

```bash
# Lint a playbook
ansible-lint playbook.yml
```

---

## 🧹 Cleanup

```bash
# Remove retry files
rm -f *.retry
```

---

## 🧾 Miscellaneous

```bash
# Display ansible version
ansible --version

# Show active ansible configuration
ansible-config dump --only-changed

# Test ping with specific user
ansible all -u ansible -m ping
```
