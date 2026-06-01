<img width="848" height="908" alt="register" src="https://github.com/user-attachments/assets/a2823fc7-d6b8-425b-b92b-992b18c917e2" />
<img width="970" height="909" alt="login" src="https://github.com/user-attachments/assets/46907529-f058-4fe3-b1a3-dff0fb8108ef" />
<img width="1009" height="956" alt="Dashboard" src="https://github.com/user-attachments/assets/d972dd98-c6b8-4b26-8da7-b23c89621195" />
# User Authentication System - Task 2

## Overview
This project is an extension of the Task 1 User Management System, upgraded to include a secure User Authentication System. It demonstrates how to securely manage users in a real-world web application by implementing registration, login, session-based access control, and a protected dashboard route.

## Technologies Used
* **Backend:** Python (v3.10+), Flask
* **Frontend:** HTML5, CSS3
* **Database:** SQLite
* **Security:** Werkzeug (for password hashing)
* **Sessions:** Flask built-in session management

## Authentication Flow Explanation
This application ensures that only registered users can access the dashboard by following a strict authentication flow:

1. **User Registration (Signup):** When a new user submits the registration form, the backend intercepts the POST request. Instead of saving the password as plain text, it uses Werkzeug's `generate_password_hash` function to securely scramble the password before storing it in the SQLite database alongside a unique username.

2. **User Login:** Upon attempting to log in, the backend queries the database for the provided username. If the user exists, it uses `check_password_hash` to compare the entered password against the hashed password stored in the database. 

3. **Session Management & Protected Dashboard:** If the login credentials are valid, the server creates a secure "session" for that user by storing their username in a temporary session cookie. When the user tries to visit the `/dashboard` route, the backend checks if this session exists. If the session is active, they are granted access. If a user tries to access the dashboard without an active session, they are automatically redirected back to the login page.

4. **Logout:** When the user clicks "Logout," the application destroys the active session by popping the user's data from the session dictionary and redirects them safely back to the login screen.

project Structure

python-fullstack-task2/
│
├── app.py

├── database.db
│

├── static/

│   └── style.css
│
└── templates/

    ├── dashboard.html
    
    ├── login.html
    
    └── register.html
