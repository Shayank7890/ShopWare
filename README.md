# 🛒 ShopWare - Full Stack E-Commerce Platform

![ShopWare](https://img.shields.io/badge/ShopWare-Full%20Stack-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)

A comprehensive full-stack e-commerce application built with **Spring Boot** backend and **React** frontend, featuring product browsing, cart management, user authentication, and complete order processing.

---

## 📋 Table of Contents

- [Features](#features)
- [Technologies](#technologies)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Backend Setup](#backend-setup)
- [Frontend Setup](#frontend-setup)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Project Status](#project-status)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features

### 🎯 Core Features
- **Product Management**: Browse, search, and filter products by categories, price, size, and color
- **Shopping Cart**: Add/remove items, manage quantities with persistent storage
- **User Authentication**: Secure signup, login with JWT-based authentication
- **OAuth 2.0 Integration**: Google Sign-In for social authentication
- **Order Processing**: Complete checkout flow with order confirmation
- **Payment Integration**: Stripe payment gateway integration
- **Admin Panel**: Product management and order tracking dashboard
- **User Account**: Profile management, address book, order history, and settings
- **Responsive Design**: Mobile-friendly UI built with Tailwind CSS

### 🔐 Security Features
- JWT token-based authentication
- Spring Security for backend authorization
- Password encryption with bcrypt
- CORS configuration
- Protected API endpoints

### 📊 Admin Features
- Product creation and management
- Category management
- Order tracking and management
- User management

---

## 🛠️ Technologies

### Frontend Stack
| Technology | Purpose |
|-----------|---------|
| **React 18.2** | UI Framework |
| **Redux Toolkit** | State Management |
| **Tailwind CSS** | Styling Framework |
| **Axios** | HTTP Client |
| **React Router v6** | Client-side Routing |
| **React Hook Form** | Form Management |
| **Stripe React** | Payment Processing |
| **React Modal** | Modal Dialogs |

### Backend Stack
| Technology | Purpose |
|-----------|---------|
| **Spring Boot 3.3.2** | Web Framework |
| **Spring Data JPA** | ORM & Database Access |
| **Spring Security** | Authentication & Authorization |
| **JWT (JSON Web Tokens)** | Token-based Auth |
| **Maven** | Build Tool |
| **Lombok** | Code Generation |

### Database & Infrastructure
| Technology | Purpose |
|-----------|---------|
| **PostgreSQL** | Primary Database |
| **AWS S3** | File Storage (Optional) |
| **Stripe API** | Payment Processing |

---

## 📁 Project Structure

```
ShopWare/
├── backend/                          # Spring Boot Backend
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/thecodereveal/shopware/
│   │   │   │   ├── ShopeaseApplication.java
│   │   │   │   ├── config/           # Spring configurations
│   │   │   │   ├── controllers/      # REST Controllers
│   │   │   │   ├── entities/         # JPA Entities
│   │   │   │   ├── repositories/     # Data Access Layer
│   │   │   │   ├── services/         # Business Logic
│   │   │   │   ├── security/         # Security Configuration
│   │   │   │   ├── exceptions/       # Custom Exceptions
│   │   │   │   └── specification/    # JPA Specifications
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   └── test/
│   ├── pom.xml                       # Maven Dependencies
│   ├── mvnw & mvnw.cmd              # Maven Wrapper
│
├── UI/                               # React Frontend
│   ├── src/
│   │   ├── components/               # Reusable Components
│   │   │   ├── Navigation/
│   │   │   ├── Footer/
│   │   │   ├── Card/
│   │   │   ├── Filters/
│   │   │   ├── Buttons/
│   │   │   └── common/               # SVG Icons & Common UI
│   │   ├── pages/                    # Page Components
│   │   │   ├── ProductListPage/
│   │   │   ├── ProductDetailPage/
│   │   │   ├── Cart/
│   │   │   ├── Checkout/
│   │   │   ├── Account/
│   │   │   ├── AdminPanel/
│   │   │   └── Authentication/
│   │   ├── api/                      # API Service Calls
│   │   ├── store/                    # Redux Store
│   │   │   ├── features/             # Redux Slices
│   │   │   └── actions/              # Redux Actions
│   │   ├── routes/                   # Route Configuration
│   │   ├── utils/                    # Utility Functions
│   │   ├── assets/                   # Images & Fonts
│   │   └── styles/                   # CSS Files
│   ├── public/
│   ├── package.json
│   └── tailwind.config.js
│
├── shopware.postman_collection.json  # API Documentation
├── LICENSE
└── README.md
```

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

### For Backend:
- **Java 17** or higher
- **Maven 3.6+** (or use Maven Wrapper included)
- **PostgreSQL 12+**

### For Frontend:
- **Node.js 16+**
- **npm 8+** or **yarn 3+**

### Optional:
- **Git** for version control
- **Docker** for containerization
- **Postman** for API testing

---

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/ShopWare.git
cd ShopWare
```

### 2. Backend Setup

#### Step 1: Configure Database

Create a PostgreSQL database:

```sql
CREATE DATABASE shopware;
CREATE USER shopware_user WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE shopware TO shopware_user;
```

#### Step 2: Update Backend Configuration

Edit `backend/src/main/resources/application.properties`:

```properties
# Database Configuration
spring.datasource.url=jdbc:postgresql://localhost:5432/shopware
spring.datasource.username=shopware_user
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update

# JWT Configuration
jwt.secret=your_jwt_secret_key
jwt.expiration=86400000

# Email Configuration (Gmail)
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=your_email@gmail.com
spring.mail.password=your_app_password
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true

# Stripe Configuration
stripe.api.key=your_stripe_key
stripe.webhook.secret=your_webhook_secret

# Application Settings
spring.application.name=shopware
server.port=8080
```

#### Step 3: Build Backend

```bash
cd backend
./mvnw clean install
```

Or on Windows:
```bash
cd backend
mvnw.cmd clean install
```

### 3. Frontend Setup

#### Step 1: Install Dependencies

```bash
cd UI
npm install
```

#### Step 2: Create Environment Configuration

Create a `.env` file in the `UI` folder:

```env
REACT_APP_API_BASE_URL=http://localhost:8080/api
REACT_APP_STRIPE_PUBLIC_KEY=your_stripe_public_key
```

---

## ▶️ Running the Application

### Start Backend

```bash
cd backend
./mvnw spring-boot:run
```

Backend will be available at: `http://localhost:8080`

### Start Frontend

In a new terminal:

```bash
cd UI
npm start
```

Frontend will be available at: `http://localhost:3000`

### Verify Setup

1. **Backend API**: Visit `http://localhost:8080/api/products`
2. **Frontend**: Visit `http://localhost:3000`

---

## 📚 API Documentation

### Postman Collection

Import the `shopware.postman_collection.json` file into Postman for complete API documentation.

### Key API Endpoints

#### User Management
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | User registration |
| POST | `/api/auth/login` | User login |
| GET | `/api/auth/validate` | Validate JWT token |
| GET | `/api/users/{id}` | Get user profile |
| PUT | `/api/users/{id}` | Update user profile |

#### Products
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/products` | Get all products with filters |
| GET | `/api/products/{id}` | Get product details |
| POST | `/api/products` | Create product (Admin) |
| PUT | `/api/products/{id}` | Update product (Admin) |
| DELETE | `/api/products/{id}` | Delete product (Admin) |

#### Categories
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/categories` | Get all categories |
| POST | `/api/categories` | Create category (Admin) |

#### Orders
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/orders` | Get user orders |
| POST | `/api/orders` | Create new order |
| GET | `/api/orders/{id}` | Get order details |
| PUT | `/api/orders/{id}/status` | Update order status (Admin) |

#### Cart
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/cart` | Get shopping cart |
| POST | `/api/cart/add` | Add item to cart |
| DELETE | `/api/cart/remove/{productId}` | Remove item from cart |

---

## 🗄️ Database Schema

### Core Tables

```sql
-- Users Table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    phone_number VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Products Table
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL,
    stock_quantity INT DEFAULT 0,
    category_id INT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES categories(id)
);

-- Orders Table
CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INT NOT NULL,
    total_amount DECIMAL(10, 2) NOT NULL,
    status VARCHAR(50) DEFAULT 'PENDING',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

-- Order Items Table
CREATE TABLE order_items (
    id SERIAL PRIMARY KEY,
    order_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

---

## 📊 Project Status

### ✅ Completed Features

#### Frontend
- [x] React project structure setup
- [x] Home page with hero section and product showcase
- [x] Product browsing and filtering
- [x] Shopping cart functionality
- [x] User authentication (signup/login/logout)
- [x] Checkout process
- [x] Order confirmation page
- [x] User account dashboard
- [x] Order history and tracking
- [x] Responsive design with Tailwind CSS
- [x] OAuth 2.0 (Google Sign-In)

#### Backend
- [x] Spring Boot project setup
- [x] Product API with filtering
- [x] User authentication with JWT
- [x] Order processing and management
- [x] Shopping cart management
- [x] Admin panel API
- [x] Email notifications
- [x] Payment gateway integration (Stripe)
- [x] Security with Spring Security
- [x] PostgreSQL database integration

### 🔄 In Progress / Future Enhancements

- [ ] Product reviews and ratings
- [ ] Wishlist functionality
- [ ] Advanced search with Elasticsearch
- [ ] Inventory management system
- [ ] Multiple payment gateway options (PayPal, etc.)
- [ ] Notification system
- [ ] Mobile app (React Native)
- [ ] Docker containerization
- [ ] CI/CD pipeline
- [ ] Performance optimization and caching
- [ ] Analytics dashboard

---

## 🧪 Testing

### Backend Tests

```bash
cd backend
./mvnw test
```

### Frontend Tests

```bash
cd UI
npm test
```

---

## 🔧 Configuration

### Environment Variables

#### Backend (`application.properties`)
```properties
# Server
server.port=8080
server.servlet.context-path=/api

# Database
spring.datasource.url=jdbc:postgresql://localhost:5432/shopware
spring.datasource.username=shopware_user
spring.datasource.password=password
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=false

# JWT
jwt.secret=your_very_long_secret_key_here
jwt.expiration=86400000

# Mail
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=your_email@gmail.com
spring.mail.password=your_app_password

# CORS
cors.allowed-origins=http://localhost:3000
cors.allowed-methods=GET,POST,PUT,DELETE,OPTIONS
cors.allowed-headers=*
```

#### Frontend (`.env`)
```env
REACT_APP_API_BASE_URL=http://localhost:8080/api
REACT_APP_STRIPE_PUBLIC_KEY=pk_test_...
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/AmazingFeature`
3. Commit your changes: `git commit -m 'Add AmazingFeature'`
4. Push to the branch: `git push origin feature/AmazingFeature`
5. Open a Pull Request

### Coding Standards
- Follow Spring Boot conventions for backend code
- Use functional components for React components
- Maintain consistent code formatting
- Write meaningful commit messages
- Add comments for complex logic

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📧 Contact & Support

For issues, questions, or suggestions:
- Open an [Issue](https://github.com/yourusername/ShopWare/issues)
- Email: support@shopware.com

---

## 🎓 Learning Resources

### Backend
- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Security Documentation](https://spring.io/projects/spring-security)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)

### Frontend
- [React Documentation](https://react.dev)
- [Redux Toolkit](https://redux-toolkit.js.org/)
- [Tailwind CSS](https://tailwindcss.com)
- [React Router](https://reactrouter.com/)

### Database
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

---

## 📺 Tutorial Videos

This project was built following a comprehensive tutorial series:

1. [Project Setup & Overview](https://youtu.be/p8tBD3YTCPo)
2. [Frontend Structure & Components](https://youtu.be/LdEO5nPOaa0)
3. [Backend API Development](https://youtu.be/4nGZQbY8QTI)
4. [Authentication & Security](https://youtu.be/C-JTLiisKJ4)
5. [Shopping Cart Implementation](https://youtu.be/ew4IhNzDkkE)
6. [Order Processing](https://youtu.be/MutS1GVvCnQ)
7. [Payment Integration](https://youtu.be/ctcvf8sy2PI)
8. [Admin Panel](https://youtu.be/jan3L-PhQBM)
9. [User Account Management](https://youtu.be/NFpnxve3rDY)
10. [Deployment & Production](https://youtu.be/jetR7cQJKHM)

---

## 🎉 Acknowledgments

- Spring Boot community
- React community
- All contributors and supporters

---

**Last Updated**: April 2026
**Version**: 1.0.0
**Status**: ✅ Complete



  
