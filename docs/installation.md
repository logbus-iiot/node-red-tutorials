
## 🚀 What is Node-RED?

Node-RED is a low-code programming tool for event-driven applications. It uses a visual editor to wire together devices, APIs, and services using a browser-based flow editor.

[See a GitHub IO web version](https://logbus-iiot.github.io/node-red-tutorials/installation.html)

# 📦 Node-RED Installation Guide

This guide walks you through the installation and setup of Node-RED.

---

## ✅ Prerequisites

- **Node.js** (version 14 or later)  
  [Download Node.js](https://nodejs.org/) and install it for your operating system.  
- **npm** (comes with Node.js)

---

## ⚙️ Steps to Install Node-RED

### 1. Install Node-RED Globally

Open your terminal and run:

```bash
npm install -g --unsafe-perm node-red
```

- The `--unsafe-perm` flag is recommended for environments like Linux where Node.js is installed as the root user.

---

### 2. Start Node-RED

Run the following command to start the Node-RED server:

```bash
node-red
```

---

### 3. Access the Node-RED Editor

Once Node-RED is running, open your browser and navigate to:

```
http://localhost:1880
```

You should see the Node-RED visual editor.

---

### 4. Auto-Start Node-RED on Boot (Linux)

To ensure Node-RED starts on system boot:

```bash
sudo systemctl enable nodered.service
sudo systemctl start nodered.service
```

- To check the status:

```bash
sudo systemctl status nodered.service
```

---

### 5. Updating Node-RED

To update Node-RED to the latest version:

```bash
npm update -g --unsafe-perm node-red
```

---

### 6. Changing the Port

By default, Node-RED runs on port `1880`. To change it:

1. Open the settings file (usually located at `~/.node-red/settings.js`).

2. Update the port:

```javascript
module.exports = {
    uiPort: process.env.PORT || 1880,
};
```

3. Restart Node-RED:

```bash
node-red-stop
node-red-start
```

---

## 🚑 Troubleshooting

- **Issue:** `command not found: node-red`  
  **Solution:** Ensure Node.js and npm are correctly installed, and try reinstalling Node-RED.

- **Issue:** Port is already in use  
  **Solution:** Check for running processes using that port:

```bash
sudo lsof -i :1880
```

Kill the process if necessary:

```bash
sudo kill <PID>
```

---

You’re now ready to start building flows in Node-RED! 🚀

---

## 🚀 **Steps to Push to GitHub**

### 1. Initialize the Repository (if not already done)

```bash
git init
```

---

### 2. Add Remote Repository (if not already set)

```bash
git remote add origin https://github.com/username/repository.git
```

Replace `username` and `repository` with your actual GitHub username and repository name.

---

### 3. Add Files to Git

```bash
git add .
```

---

### 4. Commit Your Changes

```bash
git commit -m "Add Node-RED documentation with Just the Docs setup"
```

---

### 5. Push to GitHub

```bash
git push -u origin main
```

---

### ✅ **If Using GitHub Pages**

1. Go to your **GitHub repository → Settings → Pages**.
2. Under **Source**, select the branch (`main` or `gh-pages`).
3. Set the folder to `/ (root)` or `/docs` depending on your structure.
4. Click **Save**.

---

Once pushed, your documentation will be live at:

```
https://<username>.github.io/<repository>/
```

---

This setup will give you a **clean, professional, and scalable documentation site** using **Just the Docs**. 🚀