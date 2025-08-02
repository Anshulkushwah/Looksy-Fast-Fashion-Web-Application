

# Looksy – Fast Fashion Web Application

**Looksy** is an AI-powered fast fashion web platform empowering trend-conscious shoppers and small to medium-scale sellers. Sellers can instantly generate clothing designs and catalog images using advanced AI (DALL·E-like models), and customers can browse, personalize, and order made-to-order sustainable fashion—dramatically lowering waste and environmental impact.

## Table of Contents

1. [Project Overview](#project-overview)  
2. [Features](#features)  
3. [Tech Stack](#tech-stack)  
4. [System Architecture](#system-architecture)  
5. [Setup & Installation](#setup--installation)  
6. [Configuration](#configuration)  
7. [Security Practices](#security-practices)  
8. [Functional Specification](#functional-specification)  
9. [Contributing](#contributing)  
10. [License](#license)  

## Project Overview

**Problem:**  
Fashion’s traditional model suffers from overproduction, waste, and high entry barriers for emerging designers. Looksy redefines this by using AI to generate catalog images for sellers and offering customers an on-demand, made-to-order buying experience.

**Solution:**  
Looksy enables sellers to generate AI-powered fashion catalogs using models like DALL·E. Orders are produced only upon purchase, reducing inventory overhead, resource waste, and eliminating the need for professional designers.

## Features

- **AI-Generated Fashion Design:** Sellers/Admins generate product images using AI.  
- **E-commerce Platform:** Full customer journey—browse, cart, checkout, payment, and reviews.  
- **Order Management:** Made-to-order; tracking and history.  
- **Secure Authentication:** OTP + password for users; secure login for admins.  
- **Responsive Admin Dashboard:** Product, category, user, and order management.  
- **Promotions Management:** Sellers/admins handle discounts and offers.  
- **Sustainability by Design:** Orders produced only after confirmed purchase.  

## Tech Stack

- **Frontend:** ReactJS (v17.0.2), JavaScript, HTML5, Bootstrap, TailwindCSS  
- **Backend:** Spring Boot (JDK 17+)  
- **Database:** MongoDB  
- **AI Integration:** DALL·E-like model (for design generation)  

## System Architecture

```
[Browser (User/Admin)]
        ↓ REST API
 [ReactJS Frontend]
        ↓ REST API
      [Spring Boot]
        ↓
     [MongoDB]
        ↑
AI Design Service (DALL·E)
```

- **Frontend:** ReactJS client-side SPA.  
- **Backend:** Spring Boot REST API server.  
- **Database:** MongoDB (store user data, product catalog, orders, etc).  
- **AI Service:** Integrates with DALL·E via backend for design/image generation.  

## Setup & Installation

### Pre-requisites

- JDK 17 or newer  
- Node.js (latest LTS recommended)  
- MongoDB running instance  
- Cloudinary/Twilio API credentials (see `.env`/`application.properties`)  
- [Configure properties securely](#security-practices)  

### Getting Started

**1. Clone the repository:**

```bash
git clone https://github.com/Anshulkushwah/Looksy-Fast-Fashion-Web-Application.git
cd Looksy-Fast-Fashion-Web-Application
```

**2. Backend (Spring Boot):**

- Copy and configure your sensitive keys/secrets to `src/main/resources/application.properties`.  
- Install dependencies and run:

```bash
# From the backend module directory
./mvnw spring-boot:run
```

**3. Frontend (React):**

```bash
# From the frontend module directory
npm install
npm start
```

**4. Database:**  

Ensure MongoDB is running (use the correct URI in your application properties).

## Configuration

**Spring Boot application.properties example:**  
_(Never commit real secrets, API keys, or production credentials to version control!)_

```properties
spring.application.name=Backend
server.port=8080

# MongoDB
spring.data.mongodb.uri=mongodb+srv://USERNAME:PASSWORD@host/db?options
spring.data.mongodb.auto-index-creation=true

# Cloudinary (for AI images)
cloudinary.cloud_name=
cloudinary.api_key=
cloudinary.api_secret=

# JWT Settings
jwt.secret=YOUR_SECRET_HERE
jwt.expiration=86400000

# Twilio (for OTP/SMS)
twilio.account.sid=
twilio.auth.token=
twilio.phone.number=

# Mail (for notifications)
spring.mail.host=smtp.gmail.com
spring.mail.port=465
spring.mail.username=
spring.mail.password=
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.ssl.enable=true
...

# Logging and debug
logging.level.org.springframework.security=DEBUG
logging.level.org.springframework.mail=DEBUG
```

**Frontend:**  
Set up `.env` for any frontend secrets/API base URL as needed.

## Security Practices

- **NEVER** commit secrets, API keys, passwords, or tokens to Git. Use environment variables or server-side secret managers.  
- For production, all sensitive configs must be supplied **via deployment environment**, not in source control.  
- See [GitHub's secret scanning and push protection guide](https://docs.github.com/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line#resolving-a-blocked-push).  
- Always rotate and revoke leaked secrets.  

## Functional Specification

See the detailed Software Requirement Specification for full details. Highlights include:

**User Features:**

- Register/login (with OTP).  
- Browse, filter, wishlist, add to cart, checkout, pay, review.  
- Track active orders, view history.  
- Manage profile.  

**Admin Features:**

- Manage products, categories, users, orders, reviews, reports.  
- Generate discounts & promotions.  
- Run AI-image generation and publish to catalog.  
- Access dashboards and analytics.  

**Common:**

- Secure authentication (JWT, role-based access).  
- SEO-optimized, responsive UI.  

## Contributing

This project is maintained solely by Anshul Kushwah. For questions or feedback, please contact directly via GitHub or email.

## License

Project developed by Anshul Kushwah under the guidance of Scientist E : NS Nathan, C-DAC Bangalore. See [LICENSE](./LICENSE) for terms.
