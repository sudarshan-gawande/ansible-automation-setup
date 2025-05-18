# 📦 Ansible Role: webserver

This Ansible role installs and configures the Apache HTTPD web server on RHEL/CentOS-based systems using a structured, modular approach.

---

## 🛠️ How to Create a Role

```bash
ansible-galaxy init webserver
```

This will scaffold the following folder structure:

```
webserver/
├── defaults/
│   └── main.yml
├── vars/
│   └── main.yml
├── tasks/
│   └── main.yml
├── handlers/
│   └── main.yml
├── templates/
│   └── index.html.j2
├── files/
│   └── example.conf
└── meta/
    └── main.yml
```

---

## ⚙️ Role Variables

### ✅ Default Variables (defaults/main.yml)

```yaml
# Default variables for webserver role
webserver_port: 80
index_file: index.html
```

### 📌 Required Variables (vars/main.yml)

```yaml
# Role-specific hardcoded variables (optional)
httpd_package: httpd
```

---

## 📜 Role Tasks (tasks/main.yml)

```yaml
---
- name: ✅ Install Apache
  yum:
    name: "{{ httpd_package }}"
    state: present
  tags: [install]

- name: 📄 Deploy custom index.html
  template:
    src: index.html.j2
    dest: /var/www/html/index.html
    mode: '0644'
  notify: restart httpd
  tags: [deploy]

- name: 🚀 Ensure Apache is running
  service:
    name: "{{ httpd_package }}"
    state: started
    enabled: true
  tags: [service]
```

---

## 🔁 Handlers (handlers/main.yml)

```yaml
---
- name: restart httpd
  service:
    name: "{{ httpd_package }}"
    state: restarted
```

---

## 🧾 Jinja2 Template (templates/index.html.j2)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Welcome to Sudarshan's Web</title>
  <style>
    body {
      background-color: #0f172a;
      color: #f8fafc;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      text-align: center;
      padding: 5% 2%;
    }

    h1 {
      font-size: 3rem;
      margin-bottom: 0.5rem;
      color: #38bdf8;
    }

    p {
      font-size: 1.2rem;
      color: #cbd5e1;
    }

    .badge {
      margin-top: 20px;
      display: inline-block;
      padding: 10px 20px;
      background-color: #1e293b;
      color: #94a3b8;
      border-radius: 5px;
      font-size: 0.95rem;
      letter-spacing: 0.5px;
    }
  </style>
</head>
<body>
  <h1>🚀 Welcome to Ansible Deployment</h1>
  <p>This page was provisioned using Ansible by <strong>Sudarshan Gawande</strong>.</p>
  <div class="badge">DevOps Engineer | Automated with ❤️</div>
</body>
</html>
```

---

## 📋 Metadata (meta/main.yml)

```yaml
---
galaxy_info:
  author: Sudarshan Gawande
  description: Role to install and manage Apache (httpd) on Linux servers
  company: Personal Project
  license: MIT

  platforms:
    - name: EL
      versions:
        - 7
        - 8

  categories:
    - web
    - system
dependencies: []
```

---

## ▶️ Example Usage in Playbook (`site.yml`)

```yaml
---
- name: Apply Webserver Role
  hosts: webservers
  become: true
  roles:
    - webserver
```

---

## ▶️ Run the Role

```bash
ansible-playbook site.yml
```

---

## 📄 License

MIT

---

## 📧 Contact  
📧 **Email**: [sudarshangawande98@gmail.com](mailto:sudarshangawande98@gmail.com)  
🔗 **GitHub**: [Sudarshan Gawande](https://github.com/sudarshan-gawande)  
🌐 **Portfolio**: [sudarshangawande.com](https://sudarshangawande.com)  
💼 **LinkedIn**: [Sudarshan Gawande](https://www.linkedin.com/in/sudarshan-gawande/)  


