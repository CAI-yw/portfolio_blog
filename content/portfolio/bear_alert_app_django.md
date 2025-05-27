---
title: Animal Alert App Update - Django Backend with PostgreSQL
date: 2025-05-26
# images:
#   - https://i.postimg.cc/JtCVb7WF/Registration-Email.png
description: "Implemented user sign-up and log-in workflows using Django’s built-in auth system and PostgreSQL."
---

## Overall Workflow

1. **Registration**

   - User completes the registration form with a **username**, **email**, and **password**.

2. **Persistence**

   - Django saves the new user in the `auth_user` table.

3. **Redirect to Login**

   - After a successful sign-up, the user is automatically taken to the login page.

4. **Authentication**
   - User submits their credentials and clicks **Sign In**.
   - On success, they are redirected to the home page, which displays an embedded Google Map.

## Key Insights and Notes

- **Built-in User Model**  
  Utilized Django’s default `auth_user` model (fields include `id`, `username`, `email`, `password`, etc.).

- **Password Security**  
  Passwords are hashed using Django’s standard password hasher (`PBKDF2 + SHA256` by default).
