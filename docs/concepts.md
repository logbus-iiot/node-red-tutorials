# 🛠️ Basic Concepts

This section introduces some of the foundational concepts of Node-RED.

---

## 🔧 What Is a Node?
Each node in Node-RED represents a specific function or capability. Common examples include:

- **Inject Node** – to trigger a flow
- **Debug Node** – to display data
- **Function Node** – to run custom JavaScript logic

---

## 🔁 What Is a Flow?
A flow is a group of connected nodes that work together to perform a task.

- Flows can span multiple tabs.
- Messages (with a `msg` object) pass between nodes.

---

## 📦 What Is a Payload?
The `msg.payload` property contains the core data passed between nodes.

Example:
```json
{
  "payload": "Hello, world!"
}
```

---

This section will grow with more examples, best practices, and visuals. Stay tuned!

