---
title: Animal Alert App Update - Email Verification
date: 2024-12-23
images:
  - https://i.postimg.cc/JtCVb7WF/Registration-Email.png
description: Implemented email verification during user registration to ensure email validity.
---

## Overall Workflow

1. The user fills out the registration form, providing a username, email, and password.

- **API Request in Postman**:  
   `POST` localhost:8080/api/auth/signup
  ```json
  {
    "username": "user1",
    "email": "user1@gmail.com",
    "password": "user1_password",
    "role": ["user"]
  }
  ```

2. The new user's information is stored in the `user` table in the database:

   | id  | username | email           | password                                                     | enabled |
   | --- | -------- | --------------- | ------------------------------------------------------------ | ------- |
   | 2   | user1    | user1@gmail.com | $2a$10$Dvm554aScTmQHefLQZOVH./tPuKccDrkmcj.b.SYK9ERQ1fYjHCvm | f       |

3. A verification email is sent to the user's email address:
   ![Sample Verification Email](https://i.postimg.cc/JtCVb7WF/Registration-Email.png "Sample Verification Email")

4. When the user clicks the verification link, the `enabled` field in the database is updated to `TRUE`:

   | id  | username | email           | password                                                     | enabled |
   | --- | -------- | --------------- | ------------------------------------------------------------ | ------- |
   | 2   | user1    | user1@gmail.com | $2a$10$Dvm554aScTmQHefLQZOVH./tPuKccDrkmcj.b.SYK9ERQ1fYjHCvm | t       |

## Key Insights and Notes

- **Testing**: We used Postman to test the integration of the email verification and signup features.
- **Data Storage**:
  - A new field, `enabled`, was added to the `user` table.
  - By default, `enabled` is set to `FALSE`.
  - Once the user's email is verified, `enabled` is updated to `TRUE`, and the user will be able to login.
