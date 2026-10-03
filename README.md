# CST8916 Assignment 1 – REST API Extension

## Abdullahi Omer - 09043215

## October 2, 2026

## Overview

This project extends the Week 2 Flask REST API by adding a `tasks` resource and a relationship between users and their tasks.

The API supports full CRUD operations for tasks, validation and error handling, user-task queries, REST Client testing, and deployment to Azure App Service.

## Technologies

- Python 3
- Flask
- Flask-CORS
- Gunicorn
- REST Client for Visual Studio Code
- Microsoft Azure App Service

## API Endpoints

### Tasks

| Method | Endpoint      | Description             | Success |
| ------ | ------------- | ----------------------- | ------- |
| GET    | `/tasks`      | Retrieve all tasks      | 200     |
| GET    | `/tasks/<id>` | Retrieve a task by ID   | 200     |
| POST   | `/tasks`      | Create a new task       | 201     |
| PUT    | `/tasks/<id>` | Update an existing task | 200     |
| DELETE | `/tasks/<id>` | Delete a task           | 204     |

### User Tasks

| Method | Endpoint            | Description                           | Success |
| ------ | ------------------- | ------------------------------------- | ------- |
| GET    | `/users/<id>/tasks` | Retrieve all tasks assigned to a user | 200     |

## Task Data Structure

Each task contains:

```json
{
  "id": 1,
  "title": "Complete Python Assignment",
  "description": "Finish the Flask REST API lab",
  "user_id": 1,
  "completed": false
}
```

- `id` – Automatically generated integer
- `title` – Required task title
- `description` – Optional task description
- `user_id` – Required ID of an existing user
- `completed` – Optional completion status, defaulting to `false`

## Validation and Error Handling

The API handles the required error cases:

- `404 Not Found` when a task does not exist
- `404 Not Found` when a user does not exist
- `400 Bad Request` when `title` or `user_id` is missing
- `400 Bad Request` when `user_id` does not reference an existing user
- `400 Bad Request` for invalid request data

## Testing

The file `test-tasks-api.http` contains REST Client requests for testing the API.

The tests cover:

1. GET all tasks
2. GET a single task
3. GET a nonexistent task
4. POST a valid task
5. POST a task with a missing required field
6. POST a task with an invalid `user_id`
7. PUT/update a task
8. DELETE a task
9. GET tasks for a specific user

Additional tests are included for error handling and Azure deployment.

## Running Locally

Clone the repository and enter the project directory:

```bash
git clone https://github.com/abdullahi-17/26F_CST8916_Week2-REST-Lab.git
cd 26F_CST8916_Week2-REST-Lab
```

Create and activate a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the Flask application:

```bash
python app.py
```

The API will be available at:

```text
http://localhost:8000
```

## Azure Deployment

The API has been deployed to Microsoft Azure App Service.

**Azure API:**

https://cst8916-api-e7a6emg4fyh6fcfe.mexicocentral-01.azurewebsites.net/

### Example Azure Endpoints

```text
GET /health
GET /tasks
GET /tasks/1
GET /users/1/tasks
```

The deployed API was tested successfully using the REST Client, including CRUD operations and error cases.

## Video Demonstration

**YouTube Demo:**  
_Add the unlisted YouTube video link here after recording._

The demonstration shows:

- The deployed Azure API
- The API running through the Azure URL
- The `test-tasks-api.http` requests
- Successful task CRUD operations
- The user-task relationship
- At least one error-handling case

## AI Disclosure

AI tools were used to assist with implementing and reviewing the tasks CRUD endpoints, validation, API testing, and deployment-related steps.

The submitted code was reviewed, tested, and understood before submission.
