# Insta_login_register_pw

This is a simple Instagram clone built with Node.js and React. It provides functionality for user registration, login, and profile management.

## Features

- User registration with validation
- User login with authentication
- Profile management
- Logout functionality

## Technologies Used

- Node.js
- Express.js
- MongoDB
- React
- bcrypt
- JWT
- email-validator


## Documentation

This section provides detailed information on the API endpoints and usage of the Instagram login application.

### API Endpoints

The following API endpoints are available:

- **POST /signup**: Register a new user.
  - Request body:
    ```json
    {
      "name": "John Doe",
      "username": "johndoe",
      "email": "johndoe@example.com",
      "password": "password123",
      "bio": "Hello, I'm John!"
    }
    ```
  - Response:
    ```json
    {
      "success": true,
      "data": {
        "_id": "610a45b2a795a301fc84d1ef",
        "name": "John Doe",
        "username": "johndoe",
        "email": "johndoe@example.com",
        "bio": "Hello, I'm John!",
        "createdAt": "2021-08-04T10:15:22.502Z",
        "updatedAt": "2021-08-04T10:15:22.502Z"
      }
    }
    ```

- **POST /signin**: Log in an existing user.
  - Request body:
    ```json
    {
      "username": "johndoe",
      "password": "password123"
    }
    ```
  - Response:
    ```json
    {
      "success": true,
      "data": {
        "_id": "610a45b2a795a301fc84d1ef",
        "name": "John Doe",
        "username": "johndoe",
        "email": "johndoe@example.com",
        "bio": "Hello, I'm John!",
        "createdAt": "2021-08-04T10:15:22.502Z",
        "updatedAt": "2021-08-04T10:15:22.502Z"
      }
    }
    ```

- **GET /user**: Get the user's profile information.
  - Request header:
    ```
    Authorization: Bearer <token>
    ```
  - Response:
    ```json
    {
      "success": true,
      "data": {
        "_id": "610a45b2a795a301fc84d1ef",
        "name": "John Doe",
        "username": "johndoe",
        "email": "johndoe@example.com",
        "bio": "Hello, I'm John!",
        "createdAt": "2021-08-04T10:15:22.502Z",
        "updatedAt": "2021-08-04T10:15:22.502Z"
      }
    }
    ```

- **GET /logout**: Log out the user.
  - Response:
    ```json
    {
      "success": true,
      "message": "Logged Out"
    }
    ```

### Authentication

Authentication is required for accessing the `/user` and `/logout` endpoints. The user must include an `Authorization` header with the value `Bearer <token>`, where `<token>` is the JWT token received after successful login.

### Error Handling

In case of any errors, the API will return a JSON response with the following structure:

```json
{
  "success": false,
  "message": "Error message here"
}

```
Register a new user
Registers a new user with the provided information.

URL: /signup
Method: POST
Request Body:

```json
{
  "name": "John Doe",
  "username": "johndoe",
  "email": "johndoe@example.com",
  "password": "password123",
  "bio": "Hello, I'm John!"
}
```

Success Response:
Code: 200 OK
Response Body:

```
{
  "success": true,
  "data": {
    "_id": "610a45b2a795a301fc84d1ef",
    "name": "John Doe",
    "username": "johndoe",
    "email": "johndoe@example.com",
    "bio": "Hello, I'm John!",
    "createdAt": "2021-08-04T10:15:22.502Z",
    "updatedAt": "2021-08-04T10:15:22.502Z"
  }
}
```

Log in an existing user
Logs in an existing user with the provided credentials.

URL: /signin
Method: POST
Request Body:

```Log in an existing user
Logs in an existing user with the provided credentials.

URL: /signin
Method: POST
Request Body:
```
Success Response:
Code: 200 OK
Response Body:

```
{
  "success": true,
  "data": {
    "_id": "610a45b2a795a301fc84d1ef",
    "name": "John Doe",
    "username": "johndoe",
    "email": "johndoe@example.com",
    "bio": "Hello, I'm John!",
    "createdAt": "2021-08-04T10:15:22.502Z",
    "updatedAt": "2021-08-04T10:15:22.502Z"
  }
}
```



