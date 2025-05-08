The **API Gateway** design pattern is a **structural pattern** used primarily in **microservices architectures** to provide a single entry point for all client requests.

---

### 🧱 **What Is It?**

An **API Gateway** is a **server** that acts as an **intermediary** between clients and backend services. It handles requests, routes them to the appropriate service, aggregates the results, and returns them to the client.

---

### ✅ **Responsibilities of an API Gateway:**

1. **Routing** – Directs requests to the appropriate microservice.
2. **Aggregation** – Combines results from multiple services into one response.
3. **Authentication & Authorization** – Validates tokens and permissions.
4. **Rate Limiting & Throttling** – Prevents abuse by limiting request frequency.
5. **Caching** – Reduces load on backend services by caching responses.
6. **Logging & Monitoring** – Tracks requests and performance.
7. **Transformation** – Converts protocols (e.g., HTTP to WebSocket) or request/response formats.

---

### 📦 **Architecture Diagram:**

```
        +---------+
        |  Client |
        +----+----+
             |
             v
      +-------------+
      | API Gateway |
      +------+------+
             |
  +----------+----------+
  |          |          |
  v          v          v
Service A  Service B  Service C
```

---

### 🧑‍💻 **Example (with Node.js + Express):**

```javascript
const express = require("express");
const app = express();
const axios = require("axios");

app.get("/user/:id", async (req, res) => {
  // Example of request routing and aggregation
  try {
    const user = await axios.get(`http://user-service/users/${req.params.id}`);
    const orders = await axios.get(`http://order-service/orders?userId=${req.params.id}`);

    res.json({
      user: user.data,
      orders: orders.data
    });
  } catch (err) {
    res.status(500).json({ message: "Error fetching data" });
  }
});

app.listen(3000, () => console.log("API Gateway listening on port 3000"));
```

---

### 🚀 **Benefits:**

* Centralized entry point for client interactions
* Simplifies client logic (clients don’t need to call multiple services)
* Enforces security and policy in one place
* Enables backend evolution (you can split/merge services without affecting clients)

---

### ⚠️ **Drawbacks:**

* Single point of failure (unless replicated)
* Adds a slight latency overhead
* Can become a bottleneck if not properly scaled

---

### 🛠 Popular Tools for Real-World API Gateways:

* **AWS API Gateway**
* **Kong**
* **NGINX**
* **Zuul (Netflix)**
* **Express Gateway (Node.js)**
* **Apigee (Google)**

---