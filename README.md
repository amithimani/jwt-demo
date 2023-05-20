Sure! Here's a simple README file for your Spring 3.0.6 JWT demo application that runs on Java 17:

---

# Spring JWT Demo Application

This is a simple demo application built with Spring 3.0.6 that showcases JWT (JSON Web Token) authentication and authorization. The application exposes two endpoints: `/authenticate` and `/admin`.

## Prerequisites

- Java 17
- Spring 3.0.6

## Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/amithimani/jwt-demo.git
   ```

2. Build the project:

   ```bash
   mvn clean package
   ```

3. Run the application:

   ```bash
   mvn spring-boot:run
   ```

   The application will start running on `http://localhost:8080`.

## Endpoints

### 1. `/authenticate` (POST)

This endpoint is used for user authentication. It requires a JSON request body with the `username` and `password` fields. If the credentials are valid, it returns a JWT token.

Example request:

```http
POST /authenticate
Content-Type: application/json

{
  "username": "your-username",
  "password": "your-password"
}
```

Example response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "token": "your-generated-jwt-token"
}
```

### 2. `/admin` (GET)

This endpoint is protected and requires authorization. It expects the `Authorization` header to be set with the JWT token obtained from the `/authenticate` endpoint. If the token is valid and the user is authorized, it returns a successful response. Otherwise, a 403 Forbidden error is thrown.

Example request:

```http
GET /admin
Authorization: Bearer your-jwt-token
```

Example response:

```http
HTTP/1.1 200 OK
Content-Type: text/plain

Welcome to the admin area!
```

If the authorization token is missing, invalid, or expired, the response will be:

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json

{
  "message": "Access denied"
}
```

---

Feel free to modify and enhance this README file to include any additional information or instructions specific to your project.
