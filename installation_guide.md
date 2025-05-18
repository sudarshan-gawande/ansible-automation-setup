# 🔧 Ansible Controller and Managed Node Setup Guide

This guide walks through the secure and industry-recommended steps to configure an **Ansible Controller** and connect it with **Managed Node(s)** using a dedicated `ansible` user.

---

## 💻 PART 1: Set Up Ansible Controller

### 🔹 Step 1.1: Create `ansible` User

```bash
sudo useradd ansible
sudo passwd ansible  
```

---

### 🔹 Step 1.2: Grant Passwordless Sudo Access

```bash
echo "ansible ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ansible
sudo chmod 440 /etc/sudoers.d/ansible
```

✅ This is the recommended way—avoid editing `/etc/sudoers` directly.

---

### 🔹 Step 1.3: Switch to `ansible` User 
sudo su - ansible


step 1.4and Generate SSH Key

```bash
ssh-keygen -t rsa -b 4096
```

✅ Press **Enter** through all prompts to accept defaults.

---

### 🔹 Step 1.4: Install Ansible

```bash
sudo yum install ansible-core -y
```

---

## 💻 PART 2: Set Up Managed Node(s)

### 🔹 Step 2.1: Create `ansible` User

```bash
sudo useradd ansible
sudo passwd ansible
```

---

### 🔹 Step 2.2: Grant Passwordless Sudo Access

```bash
echo "ansible ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ansible
sudo chmod 440 /etc/sudoers.d/ansible
```

---

### 🔹 Step 2.3: Install Python (Required by Ansible)

```bash
sudo yum install python3 -y
```

✅ Required for Ansible to function properly on the managed node.

---

## 🔐 PART 3: Enable Passwordless SSH (Controller → Managed Node)

### 🔹 Step 3.1: Copy SSH Key Manually

**On controller node:**

```bash
cat ~/.ssh/id_rsa.pub
```

**On managed node (as `ansible` user):**

```bash
sudo su - ansible

mkdir -p ~/.ssh
chmod 700 ~/.ssh
vi ~/.ssh/authorized_keys  # Paste the copied key
chmod 600 ~/.ssh/authorized_keys
```

✅ Ensures secure passwordless SSH login.

---

### 🔹 Step 3.2: Test SSH Connection

```bash
ssh ansible@private_ip
```

✅ If login works without a password prompt, you're ready to use Ansible!