# To-Do List App 📝

![Python](https://img.shields.io/badge/Python-3.10%2B-blue) ![Django](https://img.shields.io/badge/Django-5.2-brightgreen) ![License](https://img.shields.io/badge/License-MIT-yellow) ![Build](https://img.shields.io/badge/Build-Passing-brightgreen)

A Django-based task management application that allows users to register, log in, and manage their tasks, subtasks, and comments.

<img src="images/Screenshot%202025-04-10%20222451.png" alt="Project Logo" width="800" height="400">


---

## Features ✨

1. 🔒 **User Authentication**

   - Users can register and log in to the application.
   - Authentication is handled using Django's built-in user model.
2. ✅ **Task Management**

   - Users can create tasks with a title, description, and priority (High, Medium, Low).
   - Tasks are associated with the logged-in user.
   - Tasks can be marked as complete or deleted.
3. 📋 **Subtask Management**

   - Each task can have multiple subtasks.
   - Subtasks are associated with their parent task and can also be marked as complete.
4. 💬 **Commenting System**

   - Users can add comments to tasks.
   - Comments are associated with both the task and the user who created them.
5. 🔥 **Priority Levels**

   - Tasks can be assigned one of three priority levels: High, Medium, or Low.
6. 📅 **Task Ordering**

   - Tasks are ordered by their due date.
   - Comments are ordered by their creation date (newest first).

---

## Models

### Task

- **Fields**:
  - `user`: ForeignKey to the `User` model.
  - `title`: Title of the task.
  - `description`: Optional description of the task.
  - `due_date`: Automatically set when the task is created.
  - `priority`: Priority level of the task (`High`, `Medium`, `Low`).
  - `is_complete`: Boolean indicating whether the task is complete.
  - `created_at`: Timestamp when the task was created.
- **Meta**:
  - `ordering`: Tasks are ordered by `due_date`.
  - `db_table`: `task`.

### SubTask

- **Fields**:
  - `task`: ForeignKey to the `Task` model.
  - `title`: Title of the subtask.
  - `is_complete`: Boolean indicating whether the subtask is complete.
- **Meta**:
  - `db_table`: `subtask`.

### Comment

- **Fields**:
  - `task`: ForeignKey to the `Task` model.
  - `user`: ForeignKey to the `User` model.
  - `comment_text`: Text of the comment.
  - `created_at`: Timestamp when the comment was created.
- **Meta**:
  - `ordering`: Comments are ordered by `created_at` (newest first).
  - `db_table`: `comment`.

---

## Views

### Login

- **URL**: `/`
- **Description**: Handles user login. Redirects to the task list on successful login.
- **Template**: `login.html`.

### Register

- **URL**: `/register/`
- **Description**: Handles user registration. Redirects to the login page after successful registration.
- **Template**: `register.html`.

### Task List

- **URL**: `/task_list/`
- **Description**: Displays the list of tasks for the logged-in user. Allows users to:
  - Create tasks.
  - Add subtasks to tasks.
  - Add comments to tasks.
  - Delete tasks.
- **Template**: `todo_list.html`.

### Logout

- **URL**: `/logout/`
- **Description**: Logs out the user and redirects to the login page.

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/HenokDagne/taskflow.git
   cd taskflow
   ```

## Create and activate a virtual environment:

```python
python -m venv venv
.\venv\Scripts\activate
```

## Install dependencies:

```python
pip install -r requirements.txt
```

## Apply migrations:

```python
python manage.py migrate
```

## Run the development server:

```python
python manage.py runserver
```
