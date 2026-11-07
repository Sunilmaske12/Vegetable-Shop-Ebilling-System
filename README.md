# Vegetable Shop E-Billing System

A Java Spring Boot backend project for a vegetable shop billing system. It exposes REST APIs to manage shop owners, customers, products, and customer bills with their ordered items.

The project uses Spring Data JPA and Hibernate for persistence, with MySQL as the database.

## Features

- Shop owner registration and management
- Customer registration and management under a shop owner
- Product management, including product image upload and retrieval
- Retrieve products and customers by shop owner
- Customer bill creation with ordered items
- Calculate the total bill amount from item prices and quantities
- Retrieve bills for a customer
- Check shop owner email availability
- Custom resource-not-found exception handling and structured error responses

## Technology Stack

- Java 17
- Spring Boot 3.1.5
- Spring Web
- Spring Data JPA
- Hibernate
- MySQL
- Maven
- Jackson

## Project Structure

```text
EbillingSystemForVegetableShop_SpringBoot/
├── src/
│   ├── main/
│   │   ├── java/com/ebilling/shop/
│   │   │   ├── controller/
│   │   │   ├── entity/
│   │   │   ├── exception/
│   │   │   ├── repository/
│   │   │   └── EbillingSystemForVegetableShopSpringBootApplication.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
├── pom.xml
├── mvnw
└── mvnw.cmd
```

### Main domain entities

- `Shopowner` – shop owner details and associated customers and products
- `Customer` – customer details and associated bills
- `Product` – product details and image name
- `Bill_Order` – bill details, customer, ordered items, total price and amount paid
- `OrderedItem` – product name, price and quantity recorded for a bill

## Prerequisites

- JDK 17
- Apache Maven (or use the included Maven Wrapper)
- MySQL Server
- An IDE such as IntelliJ IDEA, Eclipse, or Spring Tool Suite
- Postman or another REST client for testing the APIs

## Database Configuration

1. Start your MySQL server.
2. Create a database for the application, for example:

   ```sql
   CREATE DATABASE vms;
   ```

3. Configure the database connection in `src/main/resources/application.properties`.

   Use your own local database settings. Do not commit real database passwords or other secrets to source control.

   Example:

   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/vms
   spring.datasource.username=${DB_USERNAME}
   spring.datasource.password=${DB_PASSWORD}
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
   ```

The application currently uses Hibernate schema update configuration. Review the database configuration before running it against any database containing important data.

## Build and Run

Clone the repository:

```bash
git clone https://github.com/Sunilmaske12/Project---Ebilling-System-for-Vegetable-Shop.git
```

Move into the Spring Boot application directory:

```bash
cd Project---Ebilling-System-for-Vegetable-Shop/EbillingSystemForVegetableShop_SpringBoot
```

Build the project:

```bash
./mvnw clean package
```

On Windows, use:

```bat
mvnw.cmd clean package
```

Run the application:

```bash
./mvnw spring-boot:run
```

Alternatively, run `EbillingSystemForVegetableShopSpringBootApplication` from your IDE.

The application uses Spring Boot's default port `8080` unless configured otherwise.

## API Areas

The controllers provide endpoints for these areas:

| Area | Controller | Examples of operations |
|---|---|---|
| Shop owners | `ShopownerController` | Register, retrieve, update, delete, search by name, check email |
| Customers | `CustomerController` | Create, retrieve, update, delete, retrieve customers by shop |
| Products | `ProductController` | Create, retrieve, update, delete, retrieve products by shop, upload and retrieve images |
| Bills | `BillController` | Create bills, retrieve bills, retrieve bills by customer |
| Login | `LoginController` | Customer and shop owner login examples |

Check the controller classes for the exact request paths, HTTP methods, path variables, and request formats.

## Important Configuration and Security Notes

- The checked-in project configuration contains a database password. Replace it with an environment variable or local-only configuration, and do not publish real credentials. If the password has been used for any other account or system, change it there too.
- The login controller compares passwords directly. This is a learning implementation, not secure production authentication. Production applications should use password hashing and a proper authentication mechanism.
- Product image storage currently uses a machine-specific Windows directory. Configure a suitable external storage directory for your environment before using image upload or retrieval.
- Review file-upload validation, CORS settings, authorization, and error handling before exposing the API publicly.
- This repository contains the Spring Boot backend. A separate frontend is not included in the uploaded project.

## Author

**Sunil Maske**

- GitHub: [Sunilmaske12](https://github.com/Sunilmaske12)
- LinkedIn: [Sunil Maske](https://www.linkedin.com/in/sunil-maske/)
- LeetCode: [maskesunil16](https://leetcode.com/u/maskesunil16/)
