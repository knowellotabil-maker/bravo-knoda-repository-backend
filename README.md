{
  "name": "knoda-backend",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "cors": "^2.8.5",
    "express": "^4.18.2"const express = require("express");
const cors = require("cors");

const app = express();
app.use(cors());
app.use(express.json());

// POST /register endpoint
app.post("/register", (req, res) => {
  const { email, password } = req.body;

  if (!email || !password) {
    return res.status(400).json({
      success: false,
      message: "Email and password required"
    });
  }

  res.json({
    success: true,
    message: "Received successfully",
    yourEmail: email,
    yourPassword: password
  });
});

app.get("/", (req, res) => {
  res.send("Knoda backend is running");
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));

  }
}
