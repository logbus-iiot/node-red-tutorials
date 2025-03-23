
## 🚀 What is Node-RED?

Node-RED is a low-code programming tool for event-driven applications. It uses a visual editor to wire together devices, APIs, and services using a browser-based flow editor.

[See a GitHub IO web version](https://logbus-iiot.github.io/node-red-tutorials/installation.html)

## 🐳 Node-RED Docker Cheat Sheet (with HTTPS/SSL, Flows, and Password)

### ✅ 1. Install Docker (on Raspberry Pi or Linux)

```bash
curl -sL https://get.docker.com | sh
sudo usermod -aG docker $USER
```

> 🔁 Reboot or log out/log in after adding yourself to the `docker` group.

---

### 🔐 2. Generate password hash for `settings.js`

```bash
docker run -it --rm --entrypoint bash nodered/node-red
```

Inside the container:

```bash
node -e "console.log(require('bcryptjs').hashSync('mySecurePassword123', 8))"
```

Use the resulting bcrypt hash in your `settings.js`:

```js
adminAuth: {
  type: "credentials",
  users: [{
    username: "your-username",
    password: "paste-your-bcrypt-hash-here",
    permissions: "*"
  }]
}
```

---

### 🔐 3. Generate Self-Signed SSL Certificate
Good for a 100 years with the `-days 36500`
```bash
mkdir certs
openssl req -x509 -nodes -days 36500 -newkey rsa:2048 \
  -keyout certs/privkey.pem -out certs/cert.pem \
  -subj "/CN=node-red.local"

```

This gives you:

- `certs/privkey.pem`
- `certs/cert.pem`

---

### ⚙️ 4. Create Folder Structure

```
node-red-app/
├── Dockerfile
├── settings.js     ← with HTTPS + adminAuth
├── flows/
│   └── flows.json
└── certs/
    ├── privkey.pem
    └── cert.pem
```

---

### ⚙️ 5. Modify `settings.js` for HTTPS

```js
https: {
  key: require("fs").readFileSync('/data/certs/privkey.pem'),
  cert: require("fs").readFileSync('/data/certs/cert.pem')
},
requireHttps: true,
```

Also ensure `adminAuth` is enabled.

---

### 🛠️ 6. Build Docker Image

```bash
docker build -t custom-nodered .
```

---

### 🚀 7. Run Node-RED with local `settings.js`, flows, and certs

This is the KEY part that was missing before:

```bash
docker run -d \
  --name custom-nodered \
  -p 1880:1880 \
  -v $PWD:/data \
  --restart unless-stopped \
  custom-nodered
```

> ❗ This mounts your entire `node-red-app` project folder into `/data`, ensuring `settings.js`, `flows/`, and `certs/` are all seen by Node-RED.

---

### 🧼 8. Rebuild and Restart After Changes

```bash
docker stop custom-nodered
docker rm custom-nodered
docker build -t custom-nodered .
docker run -d \
  --name custom-nodered \
  -p 1880:1880 \
  -v $PWD:/data \
  --restart unless-stopped \
  custom-nodered
```

---

### 🌐 9. Access Node-RED via HTTPS

- On the Pi:
  ```
  https://localhost:1880
  ```

- On another device:
  ```
  https://<your-pi-ip>:1880
  ```

> ⚠️ You’ll likely see a browser warning due to the self-signed cert — that’s expected.
