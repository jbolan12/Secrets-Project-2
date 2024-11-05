# Secrets-Project-2

# Express Authentication App

This project is a user authentication app built with Node.js, Express, and PostgreSQL. It supports local authentication using email and password, as well as Google OAuth 2.0 login. Users can register, log in, log out, and submit personal secrets.

## Features

- **User Registration & Login**: Register and log in with email and password.
- **Google OAuth 2.0 Login**: Sign in with Google account credentials.
- **Session Management**: User sessions are managed using Express sessions.
- **Password Security**: Passwords are hashed with bcrypt.
- **Secrets Submission**: Authenticated users can submit and view their secrets.
- **Protected Routes**: Secrets are accessible only to logged-in users.

## Prerequisites

- **Node.js** (version 12+)
- **PostgreSQL** database
- Google API credentials (for OAuth)

## Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/your-username/express-authentication-app.git
    cd express-authentication-app
    ```

2. **Install dependencies**:
    ```bash
    npm install
    ```

3. **Set up PostgreSQL**:
    - Create a PostgreSQL database.
    - In the database, create a `users` table with the following schema:
      ```sql
      CREATE TABLE users (
        id SERIAL PRIMARY KEY,
        email VARCHAR(255) UNIQUE NOT NULL,
        password VARCHAR(255),
        secret TEXT
      );
      ```

4. **Configure environment variables**:
    - Create a `.env` file in the root directory and add your configuration:
      ```plaintext
      SESSION_SECRET=your_session_secret
      PG_USER=your_pg_user
      PG_HOST=localhost
      PG_DATABASE=your_database
      PG_PASSWORD=your_pg_password
      PG_PORT=5432
      GOOGLE_CLIENT_ID=your_google_client_id
      GOOGLE_CLIENT_SECRET=your_google_client_secret
      ```

5. **Run the app**:
    ```bash
    npm start
    ```

6. **Visit**: Open your browser and go to `http://localhost:3000`.

## Routes

- **`GET /`**: Home page
- **`GET /login`**: Login page
- **`POST /login`**: Login with email and password
- **`GET /register`**: Registration page
- **`POST /register`**: Register a new account
- **`GET /logout`**: Log out and end the session
- **`GET /secrets`**: View the user's secret (protected route)
- **`GET /submit`**: Submit a new secret (protected route)
- **`GET /auth/google`**: Initiate Google OAuth login
- **`GET /auth/google/secrets`**: Google OAuth callback, redirects to `/secrets` upon success

## Code Structure

- **`app.js`**: Main application file, configures Express, routes, and passport strategies.
- **`public/`**: Public directory for static files (CSS, images).
- **`views/`**: EJS templates for rendering pages (`home.ejs`, `login.ejs`, `register.ejs`, etc.).

## Technologies Used

- **Express**: Web framework for Node.js.
- **PostgreSQL**: Database to store user information.
- **Passport.js**: Authentication middleware for handling local and Google OAuth strategies.
- **Bcrypt**: For hashing user passwords.
- **dotenv**: Loads environment variables from a `.env` file.

## Environment Variables

- `SESSION_SECRET`: Session secret key.
- `PG_USER`, `PG_HOST`, `PG_DATABASE`, `PG_PASSWORD`, `PG_PORT`: PostgreSQL connection settings.
- `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`: Google OAuth credentials.

## Error Handling

- Error handling for database operations and password hashing is included in the app and logs errors to the console.

## License

This project is licensed under the MIT License.
