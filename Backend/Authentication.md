## **1️⃣ JWT (JSON Web Token) – Secure Identity Verification**

**What it actually is:**

- JWT is just a **digitally signed JSON object** that stores user data (like ID, role, email).
- It's used for **authentication** in web apps instead of traditional **session-based login**.

### **How it works:**

- When a user logs in, the server **creates a JWT** and sends it to the client.
- The client **stores the JWT** (usually in localStorage or cookies).
- For every API request, the client sends the JWT as a **header** (`Authorization: Bearer <token>`).
- The server **verifies** the JWT (without querying the database) and allows access.

### **Example JWT Token (Decoded)**

```json
json
CopyEdit
{
  "userId": 123,
  "role": "admin",
  "exp": 1713525900
}

```

👉 JWT allows **stateless authentication**, meaning the server doesn’t need to store sessions for users.

🔥 **Practical Use:**

- Login systems in **React, Next.js, mobile apps**.
- API authentication in **backend services (Node.js, Express, Django, etc.)**.

---

## **2️⃣ OAuth – Secure Third-Party Logins (Google, Facebook, GitHub, etc.)**

**What it actually is:**

- OAuth is just a **protocol** that lets users **log in without passwords** by using another service (Google, Facebook, GitHub).
- Instead of storing user credentials, you **redirect them to Google (or another provider) to log in**.

### **How it works:**

1. User clicks "Sign in with Google."
2. Google asks, "Do you allow this app to access your profile?"
3. If the user agrees, Google **sends a secure access token** to the app.
4. The app uses that token to **fetch user details from Google**.

🔥 **Practical Use:**

- "Sign in with Google" on websites.
- Used in apps like **LinkedIn, Instagram, GitHub authentication**.

---

## **3️⃣ Encryption – Securing Sensitive Data**

**What it actually is:**

- Encryption is just **converting data into a scrambled format** so unauthorized people can’t read it.
- Only the **correct key** can decrypt and reveal the original data.

### **Types of Encryption:**

1. **Symmetric Encryption (AES)** – Same key used for encrypting & decrypting (like a password).
2. **Asymmetric Encryption (RSA)** – Public key encrypts, Private key decrypts (used in banking & SSL).

### **Example: AES Encryption**

**Original data:**

`password123`

**Encrypted data:**

`XfA4Df5GhTzP1s...` (randomized, unreadable text)

🔥 **Practical Use:**

- **SSL/TLS (HTTPS)** for secure browsing.
- **End-to-end encryption** in WhatsApp, Signal.
- **Encrypting passwords in databases** (e.g., hashing with bcrypt).

---

## **Conclusion:**

- **JWT** → Secure user authentication without sessions.
- **OAuth** → Login with Google, GitHub, etc. (Third-party login).
- **Encryption** → Secure sensitive data from hackers.
