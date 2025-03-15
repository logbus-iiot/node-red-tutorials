# Node-RED Beginner Guide

Welcome to Node-RED! This guide will help you get started with Node-RED, a flow-based development tool for visual programming, perfect for wiring together devices, APIs, and online services.

---

## 🚀 What is Node-RED?

Node-RED is a low-code programming tool for event-driven applications. It uses a visual editor to wire together devices, APIs, and services using a browser-based flow editor.

---

## 📦 Installation

### Prerequisites:
- **Node.js** (v14 or later)
- **npm** (Node Package Manager)

### Steps to Install:

1. **Install Node-RED**:
   ```bash
   npm install -g --unsafe-perm node-red
   ```

2. **Start Node-RED**:
   ```bash
   node-red
   ```

3. Open your browser and navigate to:
   ```
   http://localhost:1880
   ```

---

## 🛠️ Basic Concepts

- **Node**: The building block of Node-RED, representing a function or process (like reading a sensor or calling an API).
- **Flow**: A collection of nodes connected together to perform a task.
- **Payload**: The main body of a message object that flows between nodes.
- **Dashboard**: UI elements for interaction, available via the `node-red-dashboard` package.

---

## ✨ Creating Your First Flow

### Example: Inject and Debug

1. **Add Nodes**:
   - Drag an **Inject** node and a **Debug** node onto the canvas.
   
2. **Connect Nodes**:
   - Click and drag from the small grey circle on the **Inject** node to the **Debug** node.

3. **Configure Nodes**:
   - Double-click the **Inject** node and set the payload to "Hello, Node-RED!".
   - Click the **Done** button.

4. **Deploy the Flow**:
   - Click the **Deploy** button in the top right corner.

5. **Test the Flow**:
   - Click the button on the **Inject** node. Check the debug tab on the right to see the output.

---

## ⚙️ Common Nodes

- **Inject**: Starts a flow manually or on a schedule.
- **Debug**: Outputs information to the debug panel.
- **Function**: Processes messages with custom JavaScript.
- **HTTP Request**: Makes HTTP API calls.
- **Dashboard Nodes**: For creating UI elements (buttons, charts, etc.).

---

## 📚 Extending Node-RED

- Install additional nodes:
   ```bash
   npm install node-red-node-<package-name>
   ```
- Common extensions:
   - `node-red-dashboard` (for UI)
   - `node-red-contrib-mqtt` (for MQTT integration)

---

## 🌐 Deploying Node-RED

- **Run on Boot (Linux)**:
   ```bash
   sudo systemctl enable nodered.service
   sudo systemctl start nodered.service
   ```

- **Custom Port**:
   Edit the settings file (typically `~/.node-red/settings.js`):
   ```javascript
   module.exports = {
       uiPort: process.env.PORT || 1880,
   };
   ```

---

## 🛡️ Security Best Practices

- Set an admin username and password in `settings.js`.
- Use HTTPS for secure connections.
- Restrict network access to trusted devices.

---

## 🧩 Useful Resources

- [Node-RED Documentation](https://nodered.org/docs/)
- [Node-RED Forum](https://discourse.nodered.org/)
- [Node-RED Flows Library](https://flows.nodered.org/)

---

## 💡 Tips and Tricks

- Use the **Context Data** feature to store flow-level variables.
- Group nodes for better readability.
- Utilize the debug panel to trace message flows and troubleshoot issues.

---

Start experimenting, have fun, and build amazing integrations with Node-RED!

💬 _"Wiring together the Internet of Things, one node at a time!"_

