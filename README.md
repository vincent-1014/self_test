# Task Management API

## Overview
This is an API for a task management system, which allows clients to manage their todo tasks efficiently.

Version: 1.0.0

## Servers
- Production server: {API Reference home page URL}

## Endpoints

### **GET /tasks**
- **Summary**: Retrieve all tasks
- **Description**: Returns a list of all tasks.
- **Responses**:
  - **200**: A list of tasks
    ```json
    [
      {
        "id": 1,
        "title": "Grocery shopping",
        "description": "Buy milk and bread",
        "deadline": "2023-04-30",
        "completed": false
      }
    ]
    ```

### **POST /tasks**
- **Summary**: Create a new task
- **Description**: Creates a new task with the provided details.
- **Request Body**: Required
  - **Content-Type**: `application/json`
    ```json
    {
      "title": "Appointment",
      "description": "Dentist appointment on Wednesday",
      "deadline": "2023-05-03",
      "completed": false
    }
    ```
- **Responses**:
  - **200**: Task created
    ```json
    {
      "id": 101,
      "title": "Appointment",
      "description": "Dentist appointment on Wednesday",
      "deadline": "2023-05-03",
      "completed": false
    }
    ```

### **GET /tasks/{taskId}**
- **Parameters**:
  - **taskId** (path, required, integer): The ID of the task
- **Summary**: Retrieve a task by ID
- **Description**: Returns a single task based on the ID provided.
- **Responses**:
  - **200**: Detailed task information
    ```json
    {
      "id": 1,
      "title": "Grocery shopping",
      "description": "Buy milk and bread",
      "deadline": "2023-04-30",
      "completed": false
    }
    ```

### **PUT /tasks/{taskId}**
- **Summary**: Update an existing task
- **Description**: Updates the details of an existing task.
- **Request Body**: Required
  - **Content-Type**: `application/json`
    ```json
    {
      "title": "Grocery shopping",
      "description": "Buy milk, bread, and eggs",
      "deadline": "2023-04-30",
      "completed": true
    }
    ```
- **Responses**:
  - **200**: Task updated
    ```json
    {
      "id": 1,
      "title": "Grocery shopping",
      "description": "Buy milk, bread, and eggs",
      "deadline": "2023-04-30",
      "completed": true
    }
    ```

### **DELETE /tasks/{taskId}**
- **Summary**: Delete a task
- **Description**: Deletes a task based on the ID provided.
- **Responses**:
  - **200**: Task deleted
    ```json
    {
      "message": "Task deleted successfully"
    }
    ```

### **GET /tasks/deadline**
- **Parameters**:
  - **deadline** (query, required, date): The deadline of the tasks to retrieve
- **Summary**: Retrieve tasks by deadline
- **Description**: Returns tasks sorted by their deadlines.
- **Responses**:
  - **200**: List of tasks by deadline
    ```json
    [
      {
        "id": 4,
        "title": "Submit report",
        "description": "Annual financial report submission",
        "deadline": "2023-06-30",
        "completed": false
      }
    ]
    ```

### **GET /tasks/weekly**
- **Summary**: Retrieve weekly tasks
- **Description**: Returns tasks that are set for the current week.
- **Responses**:
  - **200**: List of weekly tasks
    ```json
    [
      {
        "id": 5,
        "title": "Team meeting",
        "description": "Weekly sync-up",
        "deadline": "2023-05-01",
        "completed": true
      }
    ]
    ```

## Schemas

### Task
- **Type**: object
- **Properties**:
  - **id**: integer
  - **title**: string
  - **description**: string
  - **deadline**: string (format: date)
  - **completed**: boolean
