# Ethar Task Management System

Welcome to the **Ethar Planner** repository! This is a robust, dynamic, and intuitive system designed to streamline workflow organization, manage complex projects, and facilitate team collaboration through a sleek, modern Light-Themed dashboard.

## 🌟 Key Capabilities

- **Intelligent Authorization (JWT):** Secure REST API endpoints protected by JSON Web Token authentication.
- **Hierarchical Access Levels:**
  - **Managers (Admin):** Full administrative control to establish new projects, generate tasks, and remove resources.
  - **Collaborators (Member):** Read-only access to workspaces with the ability to mark tasks as in-progress or completed.
- **Dynamic Task Tracking:** Kanban-style task status updates (`PENDING`, `IN_PROGRESS`, `COMPLETED`).
- **Modern User Interface:** A completely responsive glassmorphism-inspired UI featuring teal accents, built purely with HTML, CSS, and Vanilla JavaScript.

## 💻 Tech Stack Overview

- **Server-Side Engine:** Java 1.8 with Spring Boot (v2.7.18)
- **Data Persistence:** MySQL 8+ with Spring Data JPA (Hibernate)
- **Security Layer:** Spring Security 5 + JWT authentication filters
- **Client-Side:** HTML5, CSS3 Variables, Vanilla JS ES6
- **Build Tool:** Maven

## 🚀 Getting Started

### Installation Prerequisites
1. Java Development Kit (JDK 8)
2. Apache Maven
3. MySQL Database Server running locally

### Configuration Steps

**Step 1: Database Setup**
Log into your MySQL instance and provision a new database schema:
```sql
CREATE DATABASE ethar_db;
```
*(Note: Be sure to update `application.properties` to point to `ethar_db` instead of `project_manager` if you wish to use a separate database, otherwise the default config will use `project_manager`!)*

**Step 2: Environment Variables**
Ensure your local `src/main/resources/application.properties` file reflects your active MySQL username and password:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/project_manager?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=YourSecurePassword
```

**Step 3: Compilation and Execution**
Compile the Java source code and start the embedded Tomcat server:
```bash
mvn clean package
mvn spring-boot:run
```

**Step 4: Launching the App**
The frontend client is statically served. Head over to:
```
http://localhost:8080/index.html
```

## 📚 API Reference

Here are the primary endpoints available in the system:

| HTTP Method | Endpoint | Description | Auth Required |
|-------------|----------|-------------|---------------|
| `POST` | `/api/auth/signup` | Register a new user | No |
| `POST` | `/api/auth/signin` | Retrieve JWT access token | No |
| `GET` | `/api/projects` | Fetch all project workspaces | Yes |
| `POST` | `/api/projects` | Initialize a new project | Yes (Admin) |
| `DELETE` | `/api/projects/{id}` | Remove a project & its tasks | Yes (Admin) |
| `GET` | `/api/tasks/project/{id}` | Fetch tasks for a specific project | Yes |
| `POST` | `/api/tasks` | Create a new task | Yes (Admin) |
| `DELETE` | `/api/tasks/{id}` | Remove a task | Yes (Admin) |
| `PUT` | `/api/tasks/{id}/status` | Update a task's progress state | Yes |

---
*Built with Java and Spring Boot.*
