# SysAura - System Monitoring Application

SysAura is a real-time system monitoring application that provides insights into CPU, memory, disk, and network usage. It features a React frontend and a Node.js backend.

## Authors

- **Abhishek**
- **Akshatha**

## Features

- Real-time system metrics monitoring
- User authentication and authorization
- Admin and user roles
- System management
- Alerts and notifications
- WebSocket support for real-time updates
- Responsive UI with dark mode support

## Project Structure

The project is divided into two main parts:

1. **Frontend**: React application with TypeScript
2. **Backend**: Node.js server with Express

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/sysauraft.git
   cd sysauraft
   ```

2. Install frontend dependencies:
   ```
   npm install
   ```

3. Install backend dependencies:
   ```
   cd backend
   npm install
   ```

### Running the Application

1. Start the backend server:
   ```
   cd backend
   npm run dev
   ```

2. Start the frontend development server:
   ```
   # In the project root
   npm run dev
   ```

3. Open your browser and navigate to `http://localhost:5173`

## Backend API

The backend provides the following API endpoints:

### Authentication
- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user

### Metrics
- `GET /api/metrics/current` - Get current system metrics
- `GET /api/metrics/history/:systemId` - Get metrics history for a system
- `POST /api/metrics/:systemId` - Save system metrics

### Systems
- `GET /api/systems` - Get all systems (admin only)
- `GET /api/systems/user` - Get systems for current user
- `GET /api/systems/:id` - Get a single system
- `POST /api/systems` - Create a new system
- `PUT /api/systems/:id` - Update a system
- `DELETE /api/systems/:id` - Delete a system

### Alerts
- `GET /api/alerts` - Get all alerts
- `GET /api/alerts/system/:systemId` - Get alerts for a specific system
- `POST /api/alerts` - Create a new alert
- `PATCH /api/alerts/:id` - Update alert status

### Users
- `GET /api/users` - Get all users (admin only)
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update user profile
- `PUT /api/users/password` - Change password
- `PUT /api/users/email/:id` - Change email
- `PUT /api/users/role/:id` - Change user role (admin only)
- `DELETE /api/users/:id` - Delete user (admin only)

## WebSocket API

The application uses WebSockets for real-time updates. Connect to the WebSocket server at `ws://localhost:5000` and send/receive JSON messages.

### Client to Server Messages
- Authentication: `{ type: "auth", token: "jwt_token" }`
- Subscribe to system: `{ type: "subscribe", systemId: "1" }`
- Unsubscribe from system: `{ type: "unsubscribe", systemId: "1" }`

### Server to Client Messages
- Authentication success: `{ type: "auth_success", userId: 1, role: "admin" }`
- Authentication error: `{ type: "auth_error", message: "Invalid token" }`
- Subscription confirmation: `{ type: "subscribed", systemId: "1" }`
- Unsubscription confirmation: `{ type: "unsubscribed", systemId: "1" }`
- Metrics update: `{ type: "metrics", systemId: "1", data: {...}, timestamp: "..." }`
- Error: `{ type: "error", message: "Error message" }`

## Default Login Credentials

- Admin:
  - Email: admin@sysauraft.com
  - Password: admin123
