Instagram Login / Signup

1 - We installing --> npm i bcrypt cookie-parser cors dotenv email-validator express jsonwebtoken mongoose nodemon

Now using express to connect server
-->

The following code represents a basic Express server setup:
const express = require('express');
const app = express();

app.use('/', (req, res) => {
res.status(200).json({
data: 'Server running'
});
});

module.exports = app;


Usage
This code sets up a simple Express server that listens for incoming HTTP requests on the root path ("/"). When a request is received, it responds with a JSON object containing the message "Server running" and a 200 status code.

To use this server, follow the steps below:

Install Node.js: Make sure you have Node.js installed on your machine.

Install Dependencies: In the project directory, run npm install to install the necessary dependencies.

Start the Server: Run node server.js (assuming the file name is server.js) to start the server. It will listen on the default port 3000.

Test the Server: Open a web browser or use an API testing tool like Postman and navigate to http://localhost:3000/. You should see the response JSON with the message "Server running".

Dependencies
The code relies on the following external dependencies:

Express: A fast and minimalist web application framework for Node.js. It simplifies the process of creating robust web servers and handling HTTP requests.
Routes
The server has one route defined:

GET /: Returns a JSON response with a status code of 200. The response contains a data field with the value "Server running".
Response Format
The server responds with a JSON object in the following format:

{
  "data": "Server running"
}



Sure! Here's a sample documentation for the provided code:

Express Server Documentation
The following code represents a basic Express server setup:

javascript
Copy code
const express = require('express');
const app = express();

app.use('/', (req, res) => {
  res.status(200).json({
    data: 'Server running'
  });
});

module.exports = app;
Usage
This code sets up a simple Express server that listens for incoming HTTP requests on the root path ("/"). When a request is received, it responds with a JSON object containing the message "Server running" and a 200 status code.

To use this server, follow the steps below:

Install Node.js: Make sure you have Node.js installed on your machine.

Install Dependencies: In the project directory, run npm install to install the necessary dependencies.

Start the Server: Run node server.js (assuming the file name is server.js) to start the server. It will listen on the default port 3000.

Test the Server: Open a web browser or use an API testing tool like Postman and navigate to http://localhost:3000/. You should see the response JSON with the message "Server running".

Dependencies
The code relies on the following external dependencies:

Express: A fast and minimalist web application framework for Node.js. It simplifies the process of creating robust web servers and handling HTTP requests.
Routes
The server has one route defined:

GET /: Returns a JSON response with a status code of 200. The response contains a data field with the value "Server running".
Response Format
The server responds with a JSON object in the following format:

json
Copy code
{
  "data": "Server running"
}

Index file -->

require('dotenv').config();

const PORT = process.env.PORT || 5050;

const app = require('./app');

app.listen(PORT, () => {
  console.log(`Server is listening at http://localhost:${PORT}`);
});

Usage
This code sets up an Express server with environment configuration. It reads the PORT value from the environment variables using the dotenv package and starts the server on the specified port.

To use this server, follow the steps below:

Install Node.js: Make sure you have Node.js installed on your machine.

Install Dependencies: In the project directory, run npm install to install the necessary dependencies.

Set Environment Variables: Create a .env file in the project root directory and define the PORT variable with your desired port number. Alternatively, you can set the PORT variable directly in your system's environment.

Start the Server: Run node server.js (assuming the file name is server.js) to start the server. It will listen on the specified port or the default port 5050 if not provided.

Test the Server: Open a web browser or use an API testing tool like Postman and navigate to http://localhost:5050/. If the server starts successfully, you should see a console log indicating the server is listening at the specified URL.

Dependencies
The code relies on the following external dependencies:

dotenv: A zero-dependency module that loads environment variables from a .env file into process.env.
Configuration
The server configuration is handled through environment variables using the .env file. The PORT variable determines the port number on which the server will listen. If the PORT variable is not defined in the environment, it defaults to 5050.

Starting the Server
The code uses the app.listen() method to start the server. It listens for incoming HTTP requests on the specified port and logs a message to the console indicating the server is running.


------> Connecting server to database

The following code establishes a connection to a MongoDB database using Mongoose:

const mongoose = require('mongoose');

const MONGODB_URL = process.env.MONGODB_URL || 'mongodb://localhost:27017/pw_instagram';

const dataBaseConnect = () => {
  mongoose.connect(MONGODB_URL)
    .then((conn) => console.log(`Connected to Database: ${conn.connection.host}`))
    .catch((err) => console.log(err.message));
};

module.exports = dataBaseConnect;

Configuration
The database connection configuration is handled through environment variables. The MONGODB_URL variable defines the connection string for the MongoDB database. If the MONGODB_URL variable is not defined in the environment, it falls back to the default value 'mongodb://localhost:27017/pw_instagram', which connects to a local MongoDB instance on the default port.

Connecting to the Database
The dataBaseConnect function uses the mongoose.connect() method to establish a connection to the MongoDB database. It connects to the URL specified in the MONGODB_URL variable. Upon successful connection, it logs a message to the console indicating the successful connection along with the host details. If any errors occur during the connection, it logs the error message to the console.

Now modified code in app.js

const dataBaseConnect = require('./config/databaseConfig')

dataBaseConnect()
 added this to connect database


 ----> Created model for userschema

 const mongoose = require('mongoose')


const { Schema } = mongoose;

const userSchema = new Schema({
    name: {
        type: String,
        required: [true, 'user name is Required'],
        minLength: [5, 'Name must be 5 char'],
        maxLength: [15, 'Name must be less than 15 char'],
        trim: true
    },
    username: {
        type: String,
        required: [true, 'user name is Required'],
        minLength: [5, 'Name must be 5 char'],
        maxLength: [15, 'Name must be less than 15 char'],
        trim: true
    },
    email: {
        type: String,
        required: [true, 'user name is Required'],
        trim: true,
        unique:true,
        lowercase:true,
        unique:[true,'User already registerd']
    },
    password: {
        type: String,
        required: [true, 'user name is Required'],
        trim: true,
        unique:true,
        lowercase:true,
        unique:[true,'User already registerd']
    },
    bio: {
        type: String,
        required: [true, 'Bio is Required'],
    },
    forgetPasswordToken: {
        type: String,
    },
    forPasswordExpiryDate: {
        type: Date
    }
},{timestamps:true})

const userModel = mongoose.model('user',userSchema)

module.exports = userModel;

