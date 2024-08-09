# Well Predict API

## Features

- Register
- Login
- Get New Acces Token
- Logout
- Get Symptoms
- Predict
- Get Histories


## Tech

This server is built using:

- [Express.JS](https://expressjs.com/) - A framework of nodeJS that is used to create a server!
- [Visual Studio Code](https://code.visualstudio.com/) - Awesome text editor
- [Node .js](https://nodejs.org/) - Evented I/O for the backend
- [Mysql](https://www.mysql.com/) - Storage data
- [XAMPP](https://www.apachefriends.org/index.html) - Console for database at local
- [Knex](https://knexjs.org/) - Query builder
- [JWT](https://jwt.io/) - Token authentication
- [Bcrypt](https://www.npmjs.com/package/bcrypt) - For hashing and encrypted data
- [Axios](https://axios-http.com/docs/intro) - To query the machine learning API


## Installation

Well Predict API requires [Node.js](https://nodejs.org/) v18+ to run.

1. Install the dependencies and devDependencies and start the server.

```sh
cd Well-Predict-API
npm install
```

2. Change the atribute at file .env by following this:

| Properti | value |
| ------ | ------ |
| PORT | 8080 |
| DB_PORT | 3306 |
| DB_CLIENT | mysql |
| DB_HOST | localhost (local) or your ip connection from cloud sql |
| DB_USERNAME | root |
| DB_PASSWORD | your database password |
| DB_DATABASE | your database name |
| ACCES_TOKEN_KEY | your secret key for access token |
| REFRESH_TOKEN_KEY | your secret key for refresh token |

3. Open XAMPP console and then start Apache and MySql.
4. Open MySql admin and login to your MySql account (default login can enter username:'root' & password:'Just leave it blank')
5. Create a database with the same name in the .env file earlier.
6. Enter the SQL column and enter the query in the db.sql file then run it by clicking “go”.
7. Run the server
```sh
npm run dev 
```
## Well Predict Testing
- Postman collection [here](https://elements.getpostman.com/redirect?entityId=24348936-6656032c-9d34-4955-b9de-5b5c553a4658&entityType=collection)

## Documentation for feature

Public API:
- Method POST:
    1. Register --> {{url}}/v1/user/predict
        - receive attribute name, email, and password
        - response if success: 
            {
                code: '200',
                status: 'success',
                data:{
                    message: 'Register succes. please log in'
                }
    2. Login --> {{url}}/v1/user/login
        - receive attribute name and password
        - response if success:
            {
                    code: '200',
                    status: 'ok',
                    data: {
                        accesToken: accesToken,
                        refreshToken: refreshToken
                    }
    
Private API
- Method POST
    1. Get New Acces Token --> {{url}}/v1/user/token
        - receive header authorization with value from variable refreshToken
        - response if success:
        {
        code: '200',
        status: 'success',
        data: {
            accesToken: accesToken
        }
    2. Logout --> {{url}}/v1/user/logout
        - receive header authorization with value from variable refreshToken
        - response if success:
        {
                code: '200',
                status: 'succes',
                data:{
                    message: 'Sign out success'
                }
    3. Predict --> {{url}}/v1/user/predict
        - receive header authorization with value from variable accessToken
        - response if success:
        {
            code: '200',
            status: 'ok',
            data: {
                result: finalResult[0]
            }

- Method GET
    1. Get Symptoms --> {{url}}/v1/user/symptoms
        - receive header authorization with value from variable accessToken
        - response if success :
        {
        code: '200',
        status: 'ok',
        symptoms : symptoms
    }
    2. Get Histories --> {{url}}/v1/user/getHistories
        - receive header authorization with value from variable accessToken
        - response if success:
        {
            code: '200',
            status: 'success',
            data : parsedHistories
        }

