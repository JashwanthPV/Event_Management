# Event_Management
collaborator email:- developer@webknot.in

Here's a basic structure for the documentation to include setup instructions and API details for my Event Management project.

---

# Event Management Dashboard Documentation

## Table of Contents

1. [Project Setup Instructions](#project-setup-instructions)
2. [API Details](#api-details)

---

## 1. Project Setup Instructions

### Prerequisites

Ensure the following software is installed on your system before setting up the project:

- **Python** 3.x or higher
- **MySQL** Database
- **Git** (for cloning the repository)
- **Node.js** (if needed for frontend dependencies)
- **Virtual Environment** (recommended for Python projects)

### Step 1: Clone the Repository

Clone the project from GitHub:

```bash
git clone https://github.com/JashwanthPV/Event_Management.git
cd Event_Management
```

### Step 2: Install Dependencies

#### Backend (Python/Flask)

Create and activate a virtual environment:

```bash
python -m venv venv
# On Windows
venv\Scripts\activate
# On macOS/Linux
source venv/bin/activate
```

Install the required Python dependencies:

```bash
pip install -r requirements.txt
```

#### Frontend (if applicable)

If your project includes frontend dependencies (e.g., using JavaScript packages), you may need to run:

```bash
npm install
```

### Step 3: Set Up MySQL Database

1. **Create a MySQL database**: 
   You can create a database using MySQL Workbench, phpMyAdmin, or command line:

   ```sql
   CREATE DATABASE event_management;
   ```

2. **Set Up the Database Schema**:
   Run the schema migration scripts if any are provided, or create the necessary tables and relations manually.

3. **Configure Database Connection**:
   Update the connection settings (hostname, username, password, database name) in the project configuration files (likely `config.py` or `.env`).

### Step 4: Run the Project

Start the Flask server:

```bash
python app.py
```

The backend should be running on `http://localhost:5000` by default.

For frontend, if it’s a separate setup (e.g., React, Angular, or Vue), run:

```bash
npm start
```

### Step 5: Access the Application

- Open a browser and navigate to `http://localhost:5000` to access the Event Management Dashboard.
- Use `localhost:8080` if the project has frontend files served separately.

---

## 2. API Details

Here are the API endpoints developed for the Event Management project:

### 1. **User Authentication APIs**

- **POST /login**
  - **Description**: Allows users to log in (either as Attendee or Event Manager).
  - **Request Body**:
    ```json
    {
      "username": "user123",
      "password": "password123"
    }
    ```
  - **Response**:
    ```json
    {
      "status": "success",
      "user_type": "Attendee/Event Manager",
      "token": "jwt_token_here"
    }
    ```

- **POST /register**
  - **Description**: Registers a new user to the system.
  - **Request Body**:
    ```json
    {
      "username": "newUser",
      "password": "newPassword",
      "email": "user@example.com"
    }
    ```
  - **Response**:
    ```json
    {
      "status": "success",
      "message": "User registered successfully"
    }
    ```

### 2. **Event Manager APIs**

- **GET /events**
  - **Description**: Fetches a list of all events.
  - **Response**:
    ```json
    [
      {
        "event_id": 1,
        "event_name": "Tech Conference",
        "date": "2024-05-20",
        "location": "New York"
      },
      {
        "event_id": 2,
        "event_name": "Music Festival",
        "date": "2024-06-15",
        "location": "Los Angeles"
      }
    ]
    ```

- **POST /event**
  - **Description**: Creates a new event (accessible only to Event Managers).
  - **Request Body**:
    ```json
    {
      "event_name": "New Workshop",
      "date": "2024-07-01",
      "location": "San Francisco"
    }
    ```
  - **Response**:
    ```json
    {
      "status": "success",
      "message": "Event created successfully"
    }
    ```

- **PUT /event/{event_id}**
  - **Description**: Updates event details.
  - **Request Body**:
    ```json
    {
      "event_name": "Updated Workshop",
      "date": "2024-07-05",
      "location": "San Francisco"
    }
    ```

- **DELETE /event/{event_id}**
  - **Description**: Deletes an event by ID.
  - **Response**:
    ```json
    {
      "status": "success",
      "message": "Event deleted successfully"
    }
    ```

### 3. **Attendee APIs**

- **GET /attendees**
  - **Description**: Fetches the list of all attendees for a particular event.
  - **Response**:
    ```json
    [
      {
        "attendee_id": 1,
        "name": "John Doe",
        "email": "john.doe@example.com"
      },
      {
        "attendee_id": 2,
        "name": "Jane Smith",
        "email": "jane.smith@example.com"
      }
    ]
    ```

- **POST /attendee**
  - **Description**: Adds an attendee to the event (accessible by Event Managers).
  - **Request Body**:
    ```json
    {
      "event_id": 1,
      "attendee_name": "Alice Brown",
      "attendee_email": "alice@example.com"
    }
    ```

- **DELETE /attendee/{attendee_id}**
  - **Description**: Removes an attendee from the event.
  - **Response**:
    ```json
    {
      "status": "success",
      "message": "Attendee removed successfully"
    }
