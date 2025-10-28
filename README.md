# 🔐 ACE VPN - A VPN for Office

![ACE VPN Logo](https://img.shields.io/badge/ACE%20VPN-Secure%20Connection-blueviolet?style=for-the-badge)
![Java](https://img.shields.io/badge/Java-17+-orange?style=for-the-badge&logo=java)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.0+-green?style=for-the-badge&logo=springboot)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

**ACE VPN** is a secure, enterprise-grade VPN system designed for office environments. This project simulates a complete VPN infrastructure with client-server architecture, encrypted communication, and an admin dashboard for managing connections and users.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Screenshots](#screenshots)
- [Architecture](#architecture)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Development Roadmap](#development-roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 🎯 Overview

ACE VPN is a full-stack VPN solution built as a learning project to understand:
- Network security and encryption
- Client-server architecture
- Spring Boot backend development
- JavaFX desktop application development
- Database management with Hibernate
- JWT-based authentication
- Secure tunneling and data encryption

This project demonstrates real-world implementation of VPN concepts while maintaining production-ready code quality and architecture.

---

## ✨ Features

### 🔒 Security
- **AES & RSA Encryption** - End-to-end encrypted communication
- **JWT Authentication** - Secure token-based user authentication
- **BCrypt Password Hashing** - Industry-standard password security
- **SSL/TLS Support** - Encrypted data transmission

### 🖥️ Client Application
- **JavaFX Desktop GUI** - Modern, responsive desktop interface
- **Real-time Connection Status** - Live monitoring of VPN connection
- **Company Code Management** - Flexible organization-based access
- **Auto-reconnect** - Automatic connection recovery

### 🌐 Server Backend
- **RESTful APIs** - Clean, well-documented API endpoints
- **Multi-user Support** - Handle multiple concurrent connections
- **Session Management** - Track active user sessions
- **Logging & Monitoring** - Comprehensive activity logs

### 👨‍💼 Admin Dashboard
- **User Management** - Add, remove, and manage users
- **Connection Monitoring** - View active VPN connections
- **Session Logs** - Detailed connection history and analytics
- **Statistics** - Real-time metrics and usage data

---

## 📸 Screenshots

### Login Screen
![Login Screen](https://github.com/GaneshRenuse/Virtual-Private-Network-For-Office/blob/main/Main%20Window.png)
*Secure authentication with Company ID and Password*

### Main Interface - Disconnected
![Disconnected State](https://github.com/GaneshRenuse/Virtual-Private-Network-For-Office/blob/main/After%20Login.png)
*Ready to establish VPN connection*

### Main Interface - Connected
![Connected State](https://github.com/GaneshRenuse/Virtual-Private-Network-For-Office/blob/main/After%20Connection.png)
*Active VPN tunnel with encrypted communication*

### Error Handling
![Error Modal](path/to/error-screenshot.png)
*User-friendly error messages with themed modals*

---

## 🏗️ Architecture

```
┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
│                 │         │                 │         │                 │
│  ACE VPN Client │◄───────►│  ACE VPN Server │◄───────►│  MySQL Database │
│   (JavaFX UI)   │  HTTPS  │  (Spring Boot)  │   JDBC  │                 │
│                 │   JWT   │                 │         │                 │
└─────────────────┘         └─────────────────┘         └─────────────────┘
        │                           │
        │                           │
        │                    ┌──────▼──────┐
        │                    │             │
        └───────────────────►│   Admin     │
            Web Access       │  Dashboard  │
                             │  (Web UI)   │
                             └─────────────┘
```

### Data Flow
1. **Authentication**: Client sends credentials → Server validates against DB → JWT token issued
2. **Connection**: Client requests VPN tunnel → Server creates encrypted session → Tunnel established
3. **Data Transfer**: All data encrypted with AES → Transmitted through secure tunnel → Decrypted at destination
4. **Monitoring**: Admin dashboard queries server → Real-time connection data displayed

---

## 💻 Technology Stack

### Backend
- **Java 17+** - Core programming language
- **Spring Boot 3.0+** - Application framework
- **Spring Security** - Authentication & authorization
- **Hibernate ORM** - Database object-relational mapping
- **Spring Data JPA** - Data persistence layer
- **JWT (jjwt)** - JSON Web Token authentication
- **BCrypt** - Password encryption
- **Maven** - Build automation and dependency management

### Frontend (Client)
- **JavaFX 17+** - Desktop GUI framework
- **FXML** - UI markup language
- **SceneBuilder** - Visual UI design tool
- **CSS3** - Styling and theming

### Database
- **MySQL 8.0** / **MariaDB** - Relational database
- **XAMPP** - Local development environment

### Security & Networking
- **AES-256** - Symmetric encryption
- **RSA-2048** - Asymmetric encryption
- **TCP/UDP Sockets** - Network communication
- **SSL/TLS** - Secure transport layer

### Tools & DevOps
- **Git** - Version control
- **GitHub** - Code hosting and collaboration
- **Postman** - API testing
- **IntelliJ IDEA** - IDE for Java development
- **Docker** (optional) - Containerization
- **Render/Railway** - Cloud deployment platforms

---

## 📁 Project Structure

```
ace-vpn/
├── vpn-server/              # Spring Boot backend application
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/acevpn/
│   │   │   │       ├── controller/    # REST API controllers
│   │   │   │       ├── service/       # Business logic
│   │   │   │       ├── repository/    # Data access layer
│   │   │   │       ├── model/         # Entity classes
│   │   │   │       ├── security/      # JWT & encryption
│   │   │   │       └── config/        # Configuration classes
│   │   │   └── resources/
│   │   │       ├── application.properties
│   │   │       └── schema.sql
│   │   └── test/              # Unit and integration tests
│   └── pom.xml
│
├── vpn-client/              # JavaFX desktop client
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/acevpn/client/
│   │   │   │       ├── ui/            # JavaFX controllers
│   │   │   │       ├── network/       # Socket communication
│   │   │   │       └── util/          # Helper classes
│   │   │   └── resources/
│   │   │       ├── fxml/              # UI layouts
│   │   │       ├── css/               # Stylesheets
│   │   │       └── images/            # Assets
│   │   └── test/
│   └── pom.xml
│
├── vpn-common/              # Shared libraries
│   ├── src/
│   │   └── main/
│   │       └── java/
│   │           └── com/acevpn/common/
│   │               ├── encryption/    # AES/RSA utilities
│   │               ├── dto/           # Data transfer objects
│   │               └── constants/     # Shared constants
│   └── pom.xml
│
├── vpn-admin/               # Web admin dashboard
│   ├── src/
│   │   └── main/
│   │       ├── resources/
│   │       │   ├── templates/         # Thymeleaf/React
│   │       │   └── static/            # CSS, JS, images
│   └── pom.xml
│
├── docs/                    # Documentation
│   ├── API.md              # API documentation
│   ├── ARCHITECTURE.md     # System architecture
│   └── DEPLOYMENT.md       # Deployment guide
│
├── screenshots/             # Project screenshots
├── .gitignore
├── README.md
└── pom.xml                  # Parent POM
```

---

## 🚀 Installation

### Prerequisites
- Java JDK 17 or higher
- Maven 3.6+
- MySQL 8.0 or MariaDB
- XAMPP (for local MySQL)
- Git

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/ace-vpn.git
cd ace-vpn
```

### Step 2: Database Setup
1. Start XAMPP and launch MySQL
2. Create database:
```sql
CREATE DATABASE acevpn_db;
USE acevpn_db;
```
3. Run the schema script:
```bash
mysql -u root -p acevpn_db < vpn-server/src/main/resources/schema.sql
```

### Step 3: Configure Server
Edit `vpn-server/src/main/resources/application.properties`:
```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/acevpn_db
spring.datasource.username=root
spring.datasource.password=yourpassword

# Server Port
server.port=8080

# JWT Secret (change this!)
jwt.secret=your-secret-key-here
jwt.expiration=86400000
```

### Step 4: Build the Project
```bash
# Build all modules
mvn clean install

# Or build specific modules
cd vpn-server && mvn clean install
cd vpn-client && mvn clean install
```

### Step 5: Run the Server
```bash
cd vpn-server
mvn spring-boot:run
```

### Step 6: Run the Client
```bash
cd vpn-client
mvn javafx:run
```

---

## 📖 Usage

### For End Users

1. **Launch the Client Application**
   - Double-click the ACE VPN executable or run via Maven

2. **Login**
   - Enter your Company ID: `GR01120999`
   - Enter your Password: `Ganesh@1120999`
   - Click "Login"

3. **Configure Company Code**
   - The default code is pre-filled: `company.com/slrc/connectgroup`
   - You can modify this to connect to different company servers

4. **Connect to VPN**
   - Click the "Connect" button
   - Wait for status to change to "Connected"
   - Your connection is now encrypted and secure

5. **Disconnect**
   - Click "Disconnect" to end the VPN session
   - Click "Logout" to return to login screen

### For Administrators

1. **Access Admin Dashboard**
   - Navigate to `http://localhost:8080/admin`
   - Login with admin credentials

2. **Manage Users**
   - Add new users with company codes
   - Remove or disable user accounts
   - Reset passwords

3. **Monitor Connections**
   - View all active VPN sessions
   - Check connection logs
   - Analyze usage statistics

---

## 📚 API Documentation

### Authentication Endpoints

#### POST `/api/auth/login`
Authenticate user and receive JWT token.

**Request:**
```json
{
  "companyId": "GR01120999",
  "password": "Ganesh@1120999"
}
```

**Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIs...",
  "userId": "123",
  "expiresIn": 86400
}
```

### VPN Endpoints

#### POST `/api/vpn/connect`
Establish VPN tunnel connection.

**Headers:**
```
Authorization: Bearer <jwt_token>
```

**Request:**
```json
{
  "companyCode": "company.com/slrc/connectgroup"
}
```

**Response:**
```json
{
  "sessionId": "abc123",
  "status": "connected",
  "encryptionKey": "encrypted_aes_key"
}
```

#### POST `/api/vpn/disconnect`
Terminate VPN session.

#### GET `/api/vpn/status`
Check current VPN connection status.

### Admin Endpoints

#### GET `/api/admin/users`
List all registered users (Admin only).

#### GET `/api/admin/sessions`
View active VPN sessions (Admin only).

#### POST `/api/admin/users`
Create new user account (Admin only).

#### DELETE `/api/admin/users/{id}`
Remove user account (Admin only).

---

## 🗓️ Development Roadmap

### Phase 1: Week 1 - Project Setup ✅
- [ ] Java Socket Programming basics
- [ ] TCP/UDP communication
- [ ] Multi-module Maven project structure
- [ ] Basic client-server connection

### Phase 2: Week 2 - Spring Boot & REST APIs ✅
- [ ] Spring Boot setup
- [ ] REST API endpoints
- [ ] JSON handling
- [ ] Postman testing

### Phase 3: Week 3 - Database Integration 🔄
- [ ] MySQL/MariaDB setup
- [ ] Hibernate configuration
- [ ] JPA repositories
- [ ] User entity and authentication

### Phase 4: Week 4 - Security & Encryption 📅
- [ ] AES & RSA implementation
- [ ] JWT authentication
- [ ] BCrypt password hashing
- [ ] Encrypted communication

### Phase 5: Week 5 - Client Application 📅
- [ ] JavaFX UI design
- [ ] Login screen
- [ ] Connection management
- [ ] Status monitoring

### Phase 6: Week 6 - Admin Dashboard 📅
- [ ] Web-based admin panel
- [ ] User management
- [ ] Session monitoring
- [ ] Analytics and logs

### Phase 7: Week 7 - VPN Tunnel Simulation 📅
- [ ] Packet encryption/decryption
- [ ] Network routing simulation
- [ ] Multi-threading implementation
- [ ] Data flow visualization

### Phase 8: Week 8 - Deployment & Documentation 📅
- [ ] Error handling & validation
- [ ] Cloud deployment (Render/Railway)
- [ ] Complete documentation
- [ ] Demo video and screenshots

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit your changes**
   ```bash
   git commit -m "Add amazing feature"
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

### Coding Standards
- Follow Java naming conventions
- Write unit tests for new features
- Document public APIs with Javadoc
- Keep code coverage above 80%
- Use meaningful commit messages

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Your Name**
- GitHub: [@GaneshRenuse](https://github.com/GaneshRenuse)
- LinkedIn: [Ganesh Renuse](https://www.linkedin.com/in/ganesh-renuse-1a40ab1ba/)
- Email: ganesh21renuse3@gmail.com

---

## 🙏 Acknowledgments

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [JavaFX Documentation](https://openjfx.io)
- [Baeldung Tutorials](https://www.baeldung.com/)
- [GeeksforGeeks Networking Guide](https://www.geeksforgeeks.org/socket-programming-in-java/)
- Cisco AnyConnect VPN (inspiration)

---

## 📞 Support

If you have any questions or need help, please:
- Open an [issue](https://github.com/GaneshRenuse/Virtual-Private-Network-For-Office/issues)
- Email: ganesh21renuse3@gmail.com
- Join our [Discord community](https://discord.gg/wphZmJwTC4)

---

## 🌟 Star History

If you find this project useful, please give it a ⭐!

[![Star History Chart](https://api.star-history.com/svg?repos=GaneshRenuse/Virtual-Private-Network-For-Office&type=Date)](https://star-history.com/#GaneshRenuse/Virtual-Private-Network-For-Office&Date)

---

<div align="center">
  <p>Made with ❤️ by Ganesh Renuse</p>
  <p>© 2025 ACE VPN. All rights reserved.</p>
</div>