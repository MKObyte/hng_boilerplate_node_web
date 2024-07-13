# HNG Boilerplate Node.js

## Team Members
- [kingdavidHub](https://github.com/kingdavidHub)
- [iamhammyboi19](https://github.com/iamhammyboi19)
- [tulbadex](https://github.com/tulbadex)
- [MKObyte](https://github.com/MKObyte)
- [Ibrahim4Grace](https://github.com/Ibrahim4Grace)


## Introduction
This project is part of the HNG Stage 3 Backend Task. Our team has chosen to work with the Node.js boilerplate repository. The objective of this project is to collaboratively design a comprehensive API using OpenAPI and create a robust and well-structured database blueprint/design.

## API Design
The API design follows the OpenAPI 3.1.0 specification. Below are the endpoints and their respective details:

### Authentication
- **POST /auth/register**
  - Registers a new user
  - Request Body:
    ```json
    {
      "username": "string",
      "email": "string",
      "password": "string",
      "first_name": "string",
      "last_name": "string"
    }
    ```
  - Response:
    ```json
    {
      "id": "int",
      "username": "string",
      "email": "string",
      "first_name": "string",
      "last_name": "string",
      "created_at": "timestamp"
    }
    ```

- **POST /auth/login**
  - Logs a user in
  - Request Body:
    ```json
    {
      "username_or_email": "string",
      "password": "string"
    }
    ```
  - Response:
    ```json
    {
      "token": "string"
    }
    ```

- **POST /auth/reset-password**
  - Resets the password of the user

- **PUT /auth/change-password**
  - Changes the password of the authenticated user

- **POST /auth/logout**
  - Logs out the authenticated user

### Users
- **GET /api/users/{user_id}**
  - Returns a single user

- **GET /api/profile**
  - Returns the data of the authenticated user

- **PUT /api/profile**
  - Updates the profile of the authenticated user

### Organizations
- **GET /api/organisations**
  - Returns all the organizations of the authenticated user

- **GET /api/organisations/{org_id}**
  - Returns the data of the organization

- **POST /api/organisations/{org_id}**
  - Adds a user to the organization

- **POST /api/organisations**
  - Creates a new organization

- **DELETE /api/organisations/{org_id}**
  - Deletes the organization

- **GET /api/organisations/{org_id}/users**
  - Gets all users of the organization

### Notifications
- **GET /api/notifications**
  - Gets all notifications of the authenticated user

- **GET /api/notifications/{notification_id}**
  - Returns the details of the notification

- **POST /api/notifications**
  - Sends a new notification

- **DELETE /api/notifications/{notification_id}**
  - Deletes the notification

### Payments
- **GET /api/payments**
  - Returns all the payments of the authenticated user

- **POST /api/payments**
  - Creates a new payment for the authenticated user

- **GET /api/payments/{payment_id}**
  - Gets a single payment

- **DELETE /api/payments/{payment_id}**
  - Deletes a single payment

- **GET /api/payments-providers**
  - Returns all the available payments providers

- **GET /api/payments-providers/{provider_id}**
  - Returns a single payment provider

### Activity Logs
- **GET /api/activity-logs**
  - Returns all the activity logs of the authenticated user

- **POST /api/activity-logs**
  - Creates a new activity log

### Messaging
- **POST /api/emails/send**
  - Sends an email

### Settings
- **GET /api/settings/{userId}**
  - Gets user settings

- **PUT /api/settings/{userId}**
  - Updates user settings

### Miscellaneous
- **POST /api/waitlist**
  - Adds to waitlist

- **POST /api/invites**
  - Creates an invite

- **GET /api/random-data/{userId}**
  - Gets user random data

## Database Design
The database design is structured to support the API functionalities efficiently. Below is a high-level overview of the database schema:

### Users Table
- `id`: int (Primary Key)
- `username`: string (Unique)
- `email`: string (Unique)
- `password`: string
- `first_name`: string
- `last_name`: string
- `created_at`: timestamp

### Organizations Table
- `id`: int (Primary Key)
- `name`: string
- `created_at`: timestamp

### OrganizationUsers Table
- `organization_id`: int (Foreign Key to Organizations)
- `user_id`: int (Foreign Key to Users)
- `role`: string

### Notifications Table
- `id`: int (Primary Key)
- `user_id`: int (Foreign Key to Users)
- `message`: string
- `is_read`: boolean
- `created_at`: timestamp

### Payments Table
- `id`: int (Primary Key)
- `user_id`: int (Foreign Key to Users)
- `organization_id`: int (Foreign Key to Organizations)
- `amount`: decimal
- `currency`: string
- `status`: string
- `created_at`: timestamp

### ActivityLogs Table
- `id`: int (Primary Key)
- `user_id`: int (Foreign Key to Users)
- `action`: string
- `timestamp`: timestamp

### Settings Table
- `user_id`: int (Foreign Key to Users)
- `settings_key`: string
- `settings_value`: string

### EmailLogs Table
- `id`: int (Primary Key)
- `recipient`: string
- `subject`: string
- `body`: string
- `sent_at`: timestamp

### Waitlist Table
- `id`: int (Primary Key)
- `email`: string
- `joined_at`: timestamp

### Invites Table
- `id`: int (Primary Key)
- `user_id`: int (Foreign Key to Users)
- `invite_code`: string
- `created_at`: timestamp
- `expires_at`: timestamp

## ERD Diagram
![ERD Diagram](https://github.com/MKObyte/hng_boilerplate_node_web/blob/Tulbadex-team/ER%20diagram%20new%20print.png)


## Submission
- **Fork** the Node.js boilerplate repository from [HNGProjects](https://github.com/hngprojects/hng_boilerplate_node_web).
- **Create a new branch** using your squad's name.
- **Prepare a detailed ReadMe** file with your API design and Database Design.
- **Submit the URL** of your forked repo branch to the submission form provided.

## Contribution Guidelines
- Follow the contribution guidelines mentioned in the repository.
- Ensure all team members actively participate in the project.
- Maintain clear and concise commit messages.

## Conclusion
This stage emphasizes practical backend development skills, teamwork, and the ability to follow contribution guidelines. We look forward to creating a robust and well-structured project.
