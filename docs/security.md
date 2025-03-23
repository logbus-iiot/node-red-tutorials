# 🛡️ Security Best Practices

Securing your Node-RED instance is critical for protecting your data and system.

---

## 🔑 Admin Authentication

Enable username/password protection in your `settings.js` file:

```js
adminAuth: {
  type: "credentials",
  users: [{
    username: "admin",
    password: "<bcrypt-hash>",
    permissions: "*"
  }]
}
```

Use a tool like `bcryptjs` to generate the password hash.

---

## 🔒 HTTPS/SSL Support

Use self-signed certificates or Let's Encrypt to enable HTTPS:

```js
https: {
  key: require("fs").readFileSync("/data/certs/privkey.pem"),
  cert: require("fs").readFileSync("/data/certs/cert.pem")
},
requireHttps: true,
```

---

## 🌐 Network Hardening Tips

- Run behind a reverse proxy (e.g., Nginx, Caddy)
- Use firewall rules to limit access to the Node-RED port
- Avoid exposing Node-RED directly to the public internet

---

Stay secure! This section will expand with more best practices over time.

