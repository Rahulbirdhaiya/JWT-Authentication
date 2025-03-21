1. Added backend Folder in JWT-Authentication.
2. Selected backend under terminal with command `cd backend`.
3. Installed packages with `npm init`.
4. Installed dependencies with `npm install express cookie-parser bcrypt mongoose jsonwebtoken cors email-validator dotenv --save`.
5. Installed nodemon with `npm i nodemon --save`.
6. Added script in package.json file: `"start": "nodemon ./index.js"`.
7. Created index.js in backend folder.
8. Set the Port in backend/index.js file.
9. Imported the App Module.
10. Started the Server with `app.listen(PORT, callback function)`.
11. Created file app.js.
12. In app.js:
    1. Imported Express.
    2. Created Express App.
    3. Imported Auth Router.
    4. Added Middleware for JSON Parsing.
    5. Used Auth Router.
    6. Added Default Route.
    7. Exported the App.
13. Created router folder under backend/router.
14. Added authRouter.js file in backend/router folder.
15. In router/authRouter.js:
    1. Imported Express.
    2. Imported Signup Controller.
    3. Created Router.
    4. Defined Signup Route.
    5. Exported Router.
16. Created controller folder under backend/controller.
17. Added authController.js file in backend/controller folder.
18. In controller/authController.js:
    1. Defined Signup Function.
    2. Exported Signup Function.
19. To check, used Postman and made POST request on `http://localhost:5001/api/auth/signup`.
20. Under Postman, created collections:
    1. getUser (GET)
    2. Signup (POST)
    3. Signin (POST)
21. Created config folder under backend/config.
22. Added databaseConfig.js file in backend/config folder.
23. In config/databaseConfig.js:
    1. Imported Mongoose.
    2. Defined MongoDB URL.
    3. Created Database Connect Function.
    4. Exported Database Connect Function.
24. Created .env file in backend folder.
25. Added environment variables in .env file:
    1. PORT: The port number on which the server will listen.
    2. MONGODB_URL: The connection URL for the MongoDB database.
    3. SECRET: The secret key used for signing JWT tokens.
    4. CLIENT_URL: The URL of the client application.
26. Added comments to .env file for better understanding of each environment variable.
27. Created model folder under backend/model.
28. Added userSchema.js file in backend/model folder.
29. In model/userSchema.js:
    1. Imported Mongoose.
    2. Defined User Schema with fields for name, email, password, forgotPasswordToken, and forgotPasswordExpiryDate.
    3. Created User Model.
    4. Exported User Model.
30. Updated authController.js file.
31. In controller/authController.js:
    1. Imported User Model.
    2. Defined Signup Function to handle user signup requests.
    3. Extracted user data from the request body.
    4. Created a new user instance with the request body data.
    5. Saved the user instance to the database.
    6. Sent a success response with the saved user data.
    7. Handled duplicate email error and sent an appropriate response.
    8. Exported Signup Function.
32. In controller/authController.js:
    1. added validators on validEmail and Passsword.
33. Updated Signin in authRoute.js File.
34. Added Signin Method in authController.js.
    1. emailid and password in req.body
    2. added validators on EveryField is mandatory.
    3.  Generate JWT Token
    4. Set Cookie Options
    5. Set Cookie and Send Response
    6. Handle Errors under try and catch
35. Updated JWT web token method in userSchema.js File.
    1. Added sign signature on the token.
36. Updated authController.js file.
37. In controller/authController.js:
    1. Added validators on validEmail and password.
    2. Updated Signin method.
    3. Extracted email and password from the request body.
    4. Added validators to check if every field is mandatory.
    5. Generated JWT Token.
    6. Set Cookie Options.
    7. Set Cookie and Sent Response.
    8. Handled errors using try and catch.
38. In router/authRoute.js:
    1. added new router '/user' and Importing from authControllers
    2. Next in the authController.js created getUser fn.
    3. In that fn extracts the user ID from the request object (req.user.id) and uses the userModel to find the user in the database by their ID.
39. Created New folder middleware in backend
    1. added new file jwtauth.js
    2. Import JWT: Imported the jsonwebtoken module to handle JWT operations.
    3. Define JWT Authentication Middleware: Created a middleware function to authenticate requests using JWT.
    4. Extract Token: Extracted the token from cookies.
    5. Check Token: Checked if the token is present.
    6. Verify Token: Verified the token using the secret key from environment variables.
    7. Attach User to Request: Attached the user information from the token payload to the request object.
    8. Handle Verification Error: Sent an error response if token verification fails.
    9. Proceed to Next Middleware: Called the next middleware function in the stack.
    10. Export JWT Authentication Middleware: Exported the jwtAuth middleware for use in other files.
40. Added Cookie parser in file app.js
    1. Import cookieParser
    2. Insuring cookie is parsing before going before any routes => app.use(cookieParser());
41. Defined a GET route for /logout in authRoute.js
42. Define Logout Function in authController.js file
    1. Clear Token Cookie.
    2. Logout done on postman testing
43. Updated userSchema.js file.
    1. Added pre-save hook to hash the password before saving the user document.
    2. Added methods to the user schema.
    3. Defined jwtToken method to generate a JSON Web Token (JWT) for the user.
44. Validate User and Password by comparing bcrypt in authController.js
    1. Import Bcrypt
    2. API postman testing by signin
45. Import CORS in app.js
    1. Middleware for CORS in app.js
