Here's a sample `README.md` file for your Django REST API project:

---

# Django REST API for User, Client, and Project Management

This project is a REST API built using Django REST Framework for managing users, clients, and projects. It includes functionality for creating and managing clients, assigning users to projects, and retrieving projects assigned to logged-in users.

## Features
- **User Management**: Uses Django's default user model for user authentication.
- **Client Management**: Create, update, delete, and list clients.
- **Project Management**: Create projects under clients, assign users to projects, retrieve user-specific projects, and delete projects.
- **Authentication**: All operations are protected using token-based or session authentication (Django’s default).
  
## Technologies Used
- **Django**: Web framework
- **Django REST Framework (DRF)**: For building the RESTful API
- **MySQL**: Database
- **Python 3.12.5**

## Requirements
- Python 3.12.5
- Django 5.1.1
- Django REST Framework
- MySQL

## Installation and Setup

### 1. Clone the repository:
```bash
git clone https://github.com/aryan12072002/DRF-Client-Project-Management.git
cd DRF-Client-Project-Management #step-1
cd restproject # step2

### 2. Create a virtual environment:
```bash
python3 -m venv env
source env/bin/activate  # On Windows, use `env\Scripts\activate`
```

### 3. Install the required dependencies:
```bash
pip install -r requirements.txt
```

### 4. Database Setup:

#### For MySQL:
Make sure you have MySQL installed and a database created for the project.

In `settings.py`, update the database configuration:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'your_db_name',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

#### For PostgreSQL:
Make sure you have PostgreSQL installed and a database created.

In `settings.py`, update the database configuration:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'your_db_name',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### 5. Migrate the database:
```bash
python manage.py migrate
```

### 6. Create a superuser:
```bash
python manage.py createsuperuser
```

### 7. Run the development server:
```bash
python manage.py runserver
```

Now, you should be able to access the Django admin interface at `http://localhost:8000/admin`

## API Endpoints

### 1. Clients
- **GET /clients/**: List all clients.
- **POST /clients/**: Create a new client.
  - Request Body: 
    ```json
    { "client_name": "Company A" }
    ```
- **GET /clients/:id/**: Retrieve a client along with its projects.
- **PUT /clients/:id/**: Update a client.
- **DELETE /clients/:id/**: Delete a client.

### 2. Projects
- **POST /projects/**: Create a new project and assign users.
  - Request Body:
    ```json
    {
      "project_name": "Project A",
      "client_id": 1,
      "users": [1, 2]
    }
    ```
- **GET /projects/user-projects/**: Retrieve projects assigned to the logged-in user.
- **DELETE /projects/:id/**: Delete a project.

### Authentication
This project uses Django's default authentication system. You can use Django’s built-in session authentication or implement token-based authentication (DRF).

## Development
### Adding New Features
To add new features, follow these steps:
1. Create or modify models in `models.py`.
2. Create or modify serializers in `serializers.py`.
3. Update views in `views.py`.
4. Register routes in `urls.py`.

### Running Tests
To run the test suite, use:
```bash
python manage.py test
```
