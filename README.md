# Task Management API

A RESTful API for managing tasks with user authentication built using Node.js, Express, and MongoDB.

## Features

- User authentication using JWT
- CRUD operations for tasks
- Task status management
- User-specific task lists
- MongoDB integration

## Prerequisites

- Node.js (v14 or higher)
- MongoDB Atlas account
- npm or yarn package manager

## Getting Started

1. Clone the repository
```bash
git clone <repository-url>
cd task-management-api
```

2. Install dependencies
```bash
npm install
```

3. Configure environment variables
```bash
# Create a .env file in the root directory and add:
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
PORT=3000
```

4. Start the server
```bash
node app.js
```

## Database Setup (MongoDB Atlas)

1. Visit [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free account and new project
3. Build a cluster (free tier)
4. Create database user (Security → Database Access)
5. Allow network access (Security → Network Access → Allow Anywhere)
6. Get connection string (Cluster → Connect → Connect your application)
7. Add connection string to .env file

## API Endpoints

### Authentication

```bash
# Register new user
POST /auth/register
{
    "email": "user@example.com",
    "password": "password123"
}

# Login
POST /auth/login
{
    "email": "user@example.com",
    "password": "password123"
}
```

### Tasks (Requires Authentication Token)

```bash
# Create task
POST /tasks
{
    "title": "Task title",
    "description": "Task description"
}

# Get all tasks
GET /tasks

# Get specific task
GET /tasks/:id

# Update task status
PUT /tasks/:id
{
    "status": "completed"  # pending, in-progress, completed
}

# Delete task
DELETE /tasks/:id
```

For authenticated endpoints, include the token in headers:
```bash
Authorization: Bearer <your_token>
```

## Project Structure

```
project/
├── config/
│   └── db.js              # Database configuration
├── controllers/
│   ├── authController.js  # Auth logic
│   └── taskController.js  # Task management
├── middleware/
│   └── auth.js           # JWT middleware
├── models/
│   ├── Task.js           # Task schema
│   └── User.js           # User schema
├── routes/
│   ├── authRoutes.js     # Auth routes
│   └── taskRoutes.js     # Task routes
└── app.js                # Entry point
```

## Error Codes

- 200: Success
- 201: Created
- 400: Bad Request
- 401: Unauthorized
- 404: Not Found
- 500: Server Error

## Security Features

- Passwords hashed using bcrypt
- JWT authentication
- MongoDB injection protection
- Environment variables
- User data isolation

## License

ISC

## Contributing

1. Fork the repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Submit pull request
