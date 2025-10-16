# TaskWiser Frontend

**TaskWiser** is a modern, **light & dark-themed, role-based task management web application** built with React. It delivers a **seamless, intuitive experience** for both users and administrators, allowing efficient management of tasks, users, and analytics through **interactive dashboards and real-time updates**.

🌐 **Live Demo:** [https://taskwiser.vercel.app](https://taskwiser.vercel.app)
> **Note:** Screenshots of all dashboards in light & dark modes, and mobile & desktop views, are provided at the end of the document.
> **Note:** Backend Documentation : [https://github.com/murugaveltarun/task-wiser-backend](https://github.com/murugaveltarun/task-wiser-backend)


## 🚀 Overview

TaskWiser’s frontend empowers individuals and teams to **organize, track, and manage tasks effortlessly**. With **role-based access control**, dynamic filtering, advanced analytics, and a **responsive, modern UI**, it ensures productivity and clarity across devices and platforms.

### ✨ Key Features

- **🔐 Secure Authentication** – JWT-based login with **refresh tokens** and OAuth2 (Google and GitHub Login)
- **👥 Role-Based Dashboards** – Dedicated interfaces for Users and Administrators
- **📊 Interactive Analytics** – Real-time charts and statistics for admins using Recharts
- **🎨 Modern UI/UX** – Light and dark themes with Tailwind CSS for a polished look
- **⚡ Real-Time Updates** – Instant toast notifications for task events
- **📱 Fully Responsive** – Optimized for desktops, tablets, and mobile devices
- **🔍 Advanced Filtering & Sorting** – Effortlessly manage and prioritize tasks
- **🖥️ Clean Code Structure** – Organized components for maintainability and scalability

## 🛠️ Technologies Used

### Core Technologies

- **React 19.1.1** - Modern React with hooks and context
- **Vite 7.1.2** - Fast build tool and development server
- **React Router DOM 7.8.2** - Client-side routing
- **Tailwind CSS 4.1.12** - Utility-first CSS framework

### State Management & API

- **Context API** - Built-in React state management
- **Axios 1.11.0** - HTTP client for API communication
- **JWT Decode 4.0.0** - JWT token handling

### UI Components & Visualization

- **Lucide React 0.542.0** - Beautiful icon library
- **React Hot Toast 2.6.0** - Toast notifications
- **Recharts 3.2.1** - Data visualization library
- **React Datepicker 8.7.0** - Date selection components
- **Date-fns 4.1.0** - Date manipulation utilities

### Development Tools

- **ESLint** - Code linting and formatting
- **Vite Plugin React** - React development support

## 📁 Project Structure

```
src/
├── components/           # Reusable UI components
│   ├── context/         # React Context providers
│   │   ├── AuthContext.jsx      # Authentication state management
│   │   ├── UsersContext.jsx     # User data management
│   │   └── StatsProvider.jsx    # Statistics data provider
│   ├── error/           # Error page components
│   │   ├── Forbidden.jsx
│   │   ├── NotFound.jsx
│   │   └── Unauthorized.jsx
│   ├── model/           # Modal components
│   │   ├── ConfirmModel.jsx
│   │   └── Loading.jsx
│   ├── navigation/      # Navigation components
│   │   ├── AdminSidebar.jsx
│   │   ├── AdminNavbar.jsx
│   │   ├── UserSidebar.jsx
│   │   └── [other navigation components]
│   ├── protected/       # Route protection
│   │   └── ProtectedRoute.jsx
│   └── toast/           # Toast notification components
│       └── PublicToast.jsx
├── pages/               # Page components
│   ├── admin/           # Admin dashboard pages
│   │   ├── AdminDashboard.jsx
│   │   ├── components/  # Admin-specific components
│   │   │   ├── AllStats.jsx
│   │   │   ├── AllTasksAdmin.jsx
│   │   │   ├── AllUsers.jsx
│   │   │   └── charts/  # Analytics charts
│   │   └── pages/       # Admin page layouts
│   ├── auth/            # Authentication pages
│   │   ├── Login.jsx
│   │   ├── Register.jsx
│   │   ├── ForgotPassword.jsx
│   │   ├── ResetPassword.jsx
│   │   ├── OauthCallBack.jsx
│   │   └── AuthContext.jsx
│   ├── user/            # User dashboard pages
│   │   ├── components/  # User-specific components
│   │   │   ├── AddTask.jsx
│   │   │   ├── AllTasks.jsx
│   │   │   ├── TaskCard.jsx
│   │   │   └── ViewTask.jsx
│   │   └── pages/       # User page layouts
│   └── home/            # Landing page
│       └── Home.jsx
├── utils/               # Utility functions
│   ├── api.js           # API configuration and interceptors
│   ├── checkTokenOrRefresh.js  # Token validation
│   └── sort.js          # Sorting utilities
├── App.jsx              # Main application component
├── App.css              # Global styles
├── index.css            # CSS imports and global styles
└── main.jsx             # Application entry point
```

## 🚀 Quick Start

### Prerequisites

- **Node.js** (v18 or higher)
- **npm** (v9 or higher)
- **Git**

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/murugaveltarun/frontend.git
   cd frontend
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Environment Configuration**

   Create a `.env` file in the root directory:

   ```env
   VITE_BACKEND_URL=http://localhost:8080
   ```

4. **Start development server**

   ```bash
   npm run dev
   ```

5. **Access the application**

   Open your browser and navigate to `http://localhost:5173`

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build

## 🔧 Configuration

### Environment Variables

| Variable           | Description          | Required | Default                 |
| ------------------ | -------------------- | -------- | ----------------------- |
| `VITE_BACKEND_URL` | Backend API base URL | Yes      | `http://localhost:8080` |

### API Configuration

The application uses Axios for HTTP requests with automatic token injection:

```javascript
// API base configuration
const api = axios.create({
  baseURL: import.meta.env.VITE_BACKEND_URL,
  withCredentials: true,
});

// Automatic JWT token injection
api.interceptors.request.use((config) => {
  const token = localStorage.getItem("token");
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  return config;
});
```

## ⚠️ Quick Notes

- Make sure the backend server is running before starting the frontend.
- Verify that the `.env` file is present and correctly configured.
- The app requires Node.js v18+ and npm v9+.
- Backend must allow CORS requests from the frontend URL (`http://localhost:5173`) to ensure proper API communication (Mention your frontend URL in your backend .env file).

## 📊 Features Overview

### User Dashboard

- ✅ Create, edit, and delete personal tasks
- ✅ Advanced filtering and sorting
- ✅ Task progress tracking
- ✅ Profile management
- ✅ Responsive design for mobile devices

### Admin Dashboard

- ✅ User management and analytics
- ✅ Task oversight across all users
- ✅ Comprehensive statistics and charts
- ✅ User activity monitoring
- ✅ Data export capabilities

### Security Features

- ✅ JWT-based authentication
- ✅ OAuth2 integration (Google,Github)
- ✅ Role-based access control
- ✅ Protected routes
- ✅ Automatic token refresh
- ✅ Secure API communication

---

## 👤 User Dashboard Screenshots

### Desktop

<div style="display: flex; gap: 10px; flex-wrap: wrap;">
  <img src="images/user-dash-dark-home.png" alt="Dark Mode - Home" width=""/>
</div>

### 🌞 Light Mode

<div style="display: flex; gap: 10px; flex-wrap: wrap;">
  <img src="images/user-dash-light-home.png" alt="Light Mode - Home" width=""/>
  <img src="images/user-dash-light-task-add.png" alt="Light Mode - Add Task" width=""/>
  <img src="images/user-dash-light-task-edit.png" alt="Light Mode - Edit Task" width=""/>
  <img src="images/user-dash-light-task-view.png" alt="Light Mode - View Task" width=""/>
  <img src="images/user-dash-confirm.png" alt="Light Mode - Confirmation" width=""/>
</div>



#### Mobile

<div style="display: flex; gap: 40px; flex-wrap: wrap;">
  <img src="images/user-dash-dark-home-mobile.png" alt="Light Mode - Mobile Home" width="300"/>
    <img src="images/user-dash-dark-home-mobile-sidebar.png" alt="Dark Mode - Mobile Home Sidebar" width="300"/>
  <img src="images/user-dash-light-task-add-mobile.png" alt="Light Mode - Mobile Add Task" width="300"/>
  <img src="images/user-dash-light-task-edit-mobile.png" alt="Light Mode - Mobile Edit Task" width="300"/>
  <img src="images/user-dash-light-task-view-mobile.png" alt="Light Mode - Mobile View Task" width="300"/>
  <img src="images/user-dash-confirm-mobile.png" alt="Light Mode - Mobile Confirmation" width="300"/>
</div>

## 🏢 Admin Dashboard Screenshots

### 🌙 Dark Mode

#### Home
<img src="images/admin-dash-dark-home.png" alt="Admin Dark Home" width="100%"/>

#### Statistics
<img src="images/admin-dash-dark-stats-1.png" alt="Admin Dark Stats 1" width="100%"/>
<img src="images/admin-dash-dark-stats-2.png" alt="Admin Dark Stats 2" width="100%"/>
<img src="images/admin-dash-dark-stats-3.png" alt="Admin Dark Stats 3" width="100%"/>
<img src="images/admin-dash-dark-stats-4.png" alt="Admin Dark Stats 4" width="100%"/>
<img src="images/admin-dash-dark-stats-5.png" alt="Admin Dark Stats 5" width="100%"/>
<img src="images/admin-dash-dark-stats-summary.png" alt="Admin Dark Stats Summary" width="100%"/>

#### Tasks & Users
<img src="images/admin-dash-dark-tasks.png" alt="Admin Dark Tasks" width="100%"/>
<img src="images/admin-dash-dark-user.png" alt="Admin Dark User" width="100%"/>
<img src="images/admin-dash-dark-users.png" alt="Admin Dark Users" width="100%"/>

### 🌞 Light Mode

#### Home
<img src="images/admin-dash-light-home.png" alt="Admin Light Home" width="100%"/>

---


# TaskWiser Backend

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.5-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Java](https://img.shields.io/badge/Java-24-orange.svg)](https://openjdk.java.net/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue.svg)](https://www.mysql.com/)
[![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED.svg)](https://www.docker.com/)
[![JWT](https://img.shields.io/badge/JWT-Authentication-red.svg)](https://jwt.io/)
[![OAuth2](https://img.shields.io/badge/OAuth2-Google%20%26%20GitHub-blue.svg)](https://oauth.net/2/)

A robust, production-ready Spring Boot backend for **TaskWiser** - a comprehensive role-based task management application with JWT authentication, OAuth2 integration, and admin analytics.

> **Note:** Frontend Documentation : [https://github.com/murugaveltarun/frontend](https://github.com/murugaveltarun/frontend)

## 📋 Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Features](#features)
- [Technologies & Dependencies](#technologies--dependencies)
- [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Setup Instructions](#setup-instructions)
- [Docker Setup](#docker-setup)
- [Environment Variables](#environment-variables)

## 🎯 Overview

TaskWiser is a sophisticated task management system designed for both individual users and administrative oversight. The backend provides secure, scalable REST APIs with role-based access control, supporting traditional authentication and OAuth2 integration with Google and GitHub.

### Key Highlights

- **🔐 Multi-Authentication**: JWT tokens + OAuth2 (Google & GitHub)
- **👥 Role-Based Access**: User and Admin roles with granular permissions
- **📊 Analytics Dashboard**: Comprehensive statistics and reporting
- **🔍 Advanced Search**: Multi-criteria filtering and pagination
- **📧 Email Integration**: Password reset functionality
- **🐳 Containerized**: Docker support with MySQL integration
- **🛡️ Security**: CORS configuration, input validation, and secure password handling

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Backend       │    │   Database      │
│   (React/Vue)   │◄──►│   Spring Boot   │◄──►│   MySQL 8.0     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                              │
                              ▼
                       ┌─────────────────┐
                       │   OAuth2        │
                       │   (Google/GitHub)│
                       └─────────────────┘
```

### Core Components

- **Controllers**: REST API endpoints with request/response handling
- **Services**: Business logic and data processing
- **Repositories**: Data access layer with Spring Data JPA
- **Models**: Entity definitions with JPA annotations
- **Security**: JWT filters, OAuth2 configuration, and role-based access
- **Configuration**: CORS, security policies, and environment setup

## ✨ Features

### 🔐 Authentication & Authorization

- **User Registration & Login** with email/username validation
- **JWT Token Management** with refresh token support
- **OAuth2 Integration** with Google and GitHub
- **Password Reset** via email with secure token validation
- **Role-Based Access Control** (USER/ADMIN)

### 📝 Task Management

- **CRUD Operations** for tasks with full validation
- **Advanced Search** with multiple filter criteria:
  - Title and description search
  - Status and priority filtering
  - Due date and overdue detection
  - Completion status exclusion
- **Pagination Support** for large datasets
- **Sorting** by multiple fields and directions

### 👑 Admin Features

- **User Management** with search and pagination
- **Task Oversight** across all users
- **Analytics Dashboard** with comprehensive statistics:
  - User registration trends
  - Task completion rates
  - Priority distribution
  - Overdue task analysis
- **Bulk Operations** for user and task management

### 🛠️ Technical Features

- **RESTful API Design** with consistent response formats
- **Input Validation** and error handling
- **CORS Configuration** for frontend integration
- **Database Migration** with Hibernate DDL auto-update
- **Email Service Integration** for notifications
- **Actuator Endpoints** for monitoring and health checks

## 🛠️ Technologies & Dependencies

### Core Framework

- **Spring Boot 3.5.5** - Main application framework
- **Java 24** - Programming language
- **Maven** - Build and dependency management

### Security & Authentication

- **Spring Security** - Authentication and authorization
- **JWT (jjwt 0.12.6)** - Token-based authentication
- **Spring OAuth2 Client** - OAuth2 integration
- **BCrypt** - Password encryption

### Data Layer

- **Spring Data JPA** - Data access abstraction
- **MySQL 8.0** - Primary database
- **Hibernate** - ORM framework
- **Lombok** - Code generation

### Additional Libraries

- **Spring Boot Mail** - Email service
- **Spring Boot Actuator** - Monitoring and metrics
- **Spring Boot DevTools** - Development utilities

## 🔗 API Endpoints

### 🔐 Authentication Endpoints

| Method | Endpoint           | Description               | Access |
| ------ | ------------------ | ------------------------- | ------ |
| `GET`  | `/`                | Health check              | Public |
| `POST` | `/register`        | User registration         | Public |
| `POST` | `/login`           | User login                | Public |
| `POST` | `/refresh`         | Refresh access token      | Public |
| `POST` | `/forgot-password` | Request password reset    | Public |
| `POST` | `/reset-password`  | Reset password with token | Public |
| `GET`  | `/oauth2/success`  | OAuth2 success callback   | Public |
| `GET`  | `/oauth2/failed`   | OAuth2 failure callback   | Public |

### 📝 Task Management (User)

| Method   | Endpoint        | Description         | Access |
| -------- | --------------- | ------------------- | ------ |
| `GET`    | `/tasks`        | Get user's tasks    | User   |
| `GET`    | `/task/{id}`    | Get specific task   | User   |
| `GET`    | `/tasks/search` | Search user's tasks | User   |
| `POST`   | `/create`       | Create new task     | User   |
| `PUT`    | `/edit/{id}`    | Update task         | User   |
| `DELETE` | `/task/{id}`    | Delete task         | User   |

### 👑 Admin Endpoints

| Method   | Endpoint                     | Description                  | Access |
| -------- | ---------------------------- | ---------------------------- | ------ |
| `GET`    | `/users`                     | Get all users (paginated)    | Admin  |
| `GET`    | `/users/{id}`                | Get specific user            | Admin  |
| `GET`    | `/users/search`              | Search users                 | Admin  |
| `PUT`    | `/edit/user/{id}`            | Update user                  | Admin  |
| `GET`    | `/all-tasks`                 | Get all tasks (paginated)    | Admin  |
| `GET`    | `/users/{id}/tasks`          | Get user's tasks (paginated) | Admin  |
| `GET`    | `/users/{id}/tasks/all`      | Get all user's tasks         | Admin  |
| `GET`    | `/users/{id}/tasks/{taskid}` | Get specific task from user  | Admin  |
| `PUT`    | `/edit/task/{id}`            | Update any task              | Admin  |
| `DELETE` | `/delete/task/{id}`          | Delete any task              | Admin  |
| `GET`    | `/users/tasks/search`        | Search all tasks             | Admin  |
| `GET`    | `/users/{id}/tasks/search`   | Search user's tasks          | Admin  |
| `GET`    | `/stats`                     | Get TaskWiser analytics      | Admin  |

## 📁 Project Structure

```
src/main/java/com/tarun/TaskManagement/
├── config/                     # Configuration classes
│   ├── CorsConfig.java         # CORS configuration
│   └── SecurityConfig.java     # Security and OAuth2 setup
├── controller/                 # REST API controllers
│   ├── TasksController.java    # Task and admin endpoints
│   └── UsersController.java    # User authentication endpoints
├── exception/                  # Exception handling
│   ├── ApiResponseModel.java   # Standardized API responses
│   ├── GlobalExceptionHandler.java # Global error handling
│   └── MissingFieldException.java # Custom validation exception
├── filter/                     # Security filters
│   └── JwtFilter.java          # JWT authentication filter
├── model/                      # Entity models
│   ├── Tasks.java              # Task entity
│   ├── Users.java              # User entity
│   ├── UserPrincipal.java      # Spring Security principal
│   ├── ForgotPassword.java     # Password reset request
│   └── ResetPassword.java      # Password reset data
├── repository/                 # Data access layer
│   ├── TasksRepo.java          # Task repository
│   ├── UsersRepo.java          # User repository
│   └── ForgotPasswordRepo.java # Password reset repository
├── service/                    # Business logic
│   ├── TasksService.java       # Task business logic
│   ├── UsersService.java       # User business logic
│   ├── JwtService.java         # JWT token management
│   ├── MyUserDetailsService.java # Spring Security user service
│   └── Oauth2Service.java      # OAuth2 integration
└── TaskManagementApplication.java # Main application class
```

## 🚀 Setup Instructions

### Prerequisites

- **Java 24** or higher
- **Maven 3.6+**
- **MySQL 8.0** (or use Docker)
- **Git**

### 1. Clone the Repository

```bash
git clone https://github.com/murugaveltarun/frontend.git
cd TaskManagement
```

### 2. Build the Application

```bash
mvn clean install
```

### 3. Configure Environment Variables

Create a `.env` file in the root directory:

```env
# Database Configuration
DB_URL=jdbc:mysql://localhost:3306/task_management?createDatabaseIfNotExist=true&useSSL=false&allowPublicKeyRetrieval=true
DB_USERNAME=root
DB_PASSWORD=your_password

# JWT Configuration
SECRET_KEY=your_super_secret_jwt_key_here_make_it_long_and_secure

# OAuth2 Configuration
GOOGLE_OAUTH_CLIENT_ID=your_google_client_id
GOOGLE_OAUTH_CLIENT_SECRET=your_google_client_secret
GITHUB_OAUTH_CLIENT_ID=your_github_client_id
GITHUB_OAUTH_CLIENT_SECRET=your_github_client_secret

# Email Configuration (for password reset)
MAIL_USERNAME=your_email@gmail.com
MAIL_PASSWORD=your_app_password
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587

# Frontend URL (for CORS)
FRONTEND_URL=http://localhost:3000
```

### 4. Database Setup

Create the MySQL database:

```sql
CREATE DATABASE task_management;
```

### 5. Run the Application

```bash
java -jar target/task-wiser.jar
```

The application will be available at `http://localhost:8080`

## 🐳 Docker Setup

### Quick Start with Docker Compose

The easiest way to run TaskWiser is using the provided Docker Compose configuration:

```bash
# 1. Create your .env file (see Environment Variables section)
# 2. Run with Docker Compose
docker-compose up --build
```

This will start:

- **Backend API**: `http://localhost:8080`
- **MySQL Database**: `localhost:3307`

### Manual Docker Build

```bash
# Build the Docker image
docker build -t taskwiser-backend .

# Run with environment variables
docker run -p 8080:8080 --env-file .env taskwiser-backend
```

### Docker Compose Configuration

```yaml
services:
  app:
    build: .
    restart: always
    ports:
      - "8080:8080"
    env_file:
      - .env
    depends_on:
      - mysql

  mysql:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: kali
      MYSQL_DATABASE: task_management
    ports:
      - "3307:3306"
    volumes:
      - mysql_data:/var/lib/mysql
```

## 🔧 Environment Variables

| Variable                     | Description                    | Example                                       |
| ---------------------------- | ------------------------------ | --------------------------------------------- |
| `DB_URL`                     | MySQL database connection URL  | `jdbc:mysql://localhost:3306/task_management` |
| `DB_USERNAME`                | Database username              | `root`                                        |
| `DB_PASSWORD`                | Database password              | `your_password`                               |
| `SECRET_KEY`                 | JWT signing key (keep secure!) | `your_super_secret_key`                       |
| `GOOGLE_OAUTH_CLIENT_ID`     | Google OAuth client ID         | `your_google_client_id`                       |
| `GOOGLE_OAUTH_CLIENT_SECRET` | Google OAuth client secret     | `your_google_client_secret`                   |
| `GITHUB_OAUTH_CLIENT_ID`     | GitHub OAuth client ID         | `your_github_client_id`                       |
| `GITHUB_OAUTH_CLIENT_SECRET` | GitHub OAuth client secret     | `your_github_client_secret`                   |
| `MAIL_USERNAME`              | Email for password reset       | `your_email@gmail.com`                        |
| `MAIL_PASSWORD`              | Email password/app password    | `your_app_password`                           |
| `MAIL_HOST`                  | SMTP host                      | `smtp.gmail.com`                              |
| `MAIL_PORT`                  | SMTP port                      | `587`                                         |
| `FRONTEND_URL`               | Frontend URL for CORS          | `http://localhost:3000`                       |

---

**Built by Tarun, a Java Full Stack Developer**
