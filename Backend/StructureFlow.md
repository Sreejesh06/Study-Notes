# MERN Project Structure and Setup

## 1. **Create the Project Folder**
Open your terminal and run the following commands:
```bash
mkdir mern-project
cd mern-project
```

---

## 2. **Initialize Node.js and Install Dependencies**
- Initialize Node.js:
```bash
npm init -y
```
- Install the necessary backend dependencies:
```bash
npm install express mongoose dotenv cors
```
- Install nodemon as a dev dependency for automatic server restarts:
```bash
npm install --save-dev nodemon
```

---

## 3. **Project Folder Structure**
```
/mern-project
 ├── backend
 │    ├── config
 │    │       └── db.js         → MongoDB connection setup
 │    ├── models
 │    │       └── User.js       → MongoDB models
 │    ├── controllers
 │    │       └── userController.js → Route handlers (logic)
 │    ├── routes
 │    │       └── userRoutes.js → API routes
 │    ├── server.js             → Main entry point
 │    ├── .env                  → Environment variables
 │    └── package.json
 │
 ├── frontend
 │    ├── public
 │    ├── src
 │    │      ├── components     → Reusable components
 │    │      ├── pages          → Page-level components
 │    │      ├── App.js         → Main app file
 │    │      └── index.js       → React entry point
 │    └── package.json
 │
 └── README.md
```

---

## 4. **Backend Setup**

### MongoDB Connection (config/db.js)
```javascript
import mongoose from 'mongoose';
import dotenv from 'dotenv';

dotenv.config();

const connectDB = async () => {
  try {
    const conn = await mongoose.connect(process.env.MONGO_URI, {
      useNewUrlParser: true,
      useUnifiedTopology: true,
    });
    console.log(`MongoDB Connected: ${conn.connection.host}`);
  } catch (error) {
    console.error(`Error: ${error.message}`);
    process.exit(1);
  }
};

export default connectDB;
```

### Environment Variables (.env)
```plaintext
MONGO_URI=mongodb://localhost:27017/mernDB
PORT=5000
```

### User Model (models/User.js)
```javascript
import mongoose from 'mongoose';

const userSchema = new mongoose.Schema({
  name: { type: String, required: true },
  email: { type: String, required: true, unique: true },
  password: { type: String, required: true },
}, { timestamps: true });

const User = mongoose.model('User', userSchema);
export default User;
```

### Controller (controllers/userController.js)
```javascript
import User from '../models/User.js';

export const getUsers = async (req, res) => {
  try {
    const users = await User.find();
    res.json(users);
  } catch (error) {
    res.status(500).json({ message: 'Server Error' });
  }
};
```

### Routes (routes/userRoutes.js)
```javascript
import express from 'express';
import { getUsers } from '../controllers/userController.js';

const router = express.Router();

router.get('/', getUsers);

export default router;
```

### Server Setup (server.js)
```javascript
import express from 'express';
import dotenv from 'dotenv';
import cors from 'cors';
import connectDB from './config/db.js';
import userRoutes from './routes/userRoutes.js';

dotenv.config();
connectDB();

const app = express();

app.use(cors());
app.use(express.json());

app.use('/api/users', userRoutes);

const PORT = process.env.PORT || 5000;

app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

---

## 5. **Frontend Setup**

Go to the root folder and create the React frontend:
```bash
npx create-react-app frontend
```

Install Axios:
```bash
npm install axios
```

Add proxy to `frontend/package.json`:
```json
"proxy": "http://localhost:5000"
```

### API Call (src/App.js)
```javascript
import { useEffect, useState } from 'react';
import axios from 'axios';

function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    const fetchUsers = async () => {
      const { data } = await axios.get('/api/users');
      setUsers(data);
    };
    fetchUsers();
  }, []);

  return (
    <div>
      <h1>Users</h1>
      {users.map((user) => (
        <div key={user._id}>
          <p>{user.name} - {user.email}</p>
        </div>
      ))}
    </div>
  );
}

export default App;
```

---

## 6. **Start the Server**
- Start the backend server:
```bash
nodemon backend/server.js
```
- Start the frontend server:
```bash
npm start --prefix frontend
```

---

## 7. **Flowchart**

```plaintext
                +----------------------+
                |     MongoDB Atlas    |
                +----------------------+
                          |
                          ↓
                +----------------------+
                |      Backend         |
                | - Express.js Server  |
                | - Mongoose Models    |
                | - Controllers        |
                | - Routes             |
                +----------------------+
                          |
                          ↓
                +----------------------+
                |      API Calls       |
                | - Axios              |
                | - REST Endpoints     |
                +----------------------+
                          |
                          ↓
                +----------------------+
                |      Frontend        |
                | - React Components   |
                | - Pages              |
                | - State Management   |
                +----------------------+
```

---

## 8. **Explanation**

1. **Separation of Concerns**: Divides models, controllers, and routes into separate folders for scalability and cleaner code.
2. **Modularity**: Each module handles a specific task, making the project easier to manage.
3. **Environment Variables**: Using `.env` makes the code more secure by keeping sensitive information hidden.
4. **Proxy Setup**: Simplifies API calls in development by avoiding CORS issues.

---
