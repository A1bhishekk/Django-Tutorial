# ![Django Banner](https://static.djangoproject.com/img/logos/django-logo-positive.png)

# Setting Up a Django Project with a Virtual Environment

## Prerequisites

- Python installed on your system. You can download it from [python.org](https://www.python.org/downloads/).
- `pip` (Python package installer) installed. It usually comes with Python, but you can verify by running `pip --version` in your terminal.

## Steps

### 1. Create a Virtual Environment

A virtual environment helps you manage dependencies for your project, isolating them from other projects.

1. Open your terminal.
2. Navigate to the directory where you want to create your project:
   ```bash
   cd path/to/your/project/directory
   ```
3. Create a virtual environment:

- On Windows:
  ```bash
  python -m venv .venv
  ```
- On macOS and Linux:
  ```bash
  python3 -m venv .venv
  ```

4. The above command creates a directory named `.venv` in your project directory. This directory contains the virtual environment.

### 2. Activate the Virtual Environment

- On Windows:
  ```bash
  .\env\Scripts\activate
  ```
- On macOS and Linux:
  ```bash
  source env/bin/activate
  ```

After activation, your terminal should show `(env)` at the beginning of the prompt, indicating that the virtual environment is active.

### 3. Install Django

With the virtual environment active, install Django using `pip`:

```bash
python -m pip install Django==5.0.6
```

### 4. Create a Django Project

1. Create a new Django project by running:

```bash
django-admin startproject myproject
```

Replace myproject with the name you want for your project.

2. Navigate to the project directory:

```bash
cd myproject
```

### 5. Start the Development Server

1. Run the development server:

```bash
python manage.py runserver portnumber(optional)
```

2. Open your web browser and navigate to http://127.0.0.1:8000. You should see the Django welcome page, indicating that your project is set up correctly.

### 6. Configure static files and templates

1. Create a folder named `templates` in the root directory of your project.
2. Create a folder named `static` in the root directory of your project.
3. In the `settings.py` file of your project, add the following lines:

```python
import os # Add this import statement at the top of the file

TEMPLATES = [
    {
        ...
        'DIRS': ['templates'],
        ...
    },
]

STATIC_URL = '/static/'
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static'),
]

```

### 7. Load CSS and JavaScript files

1. Create a CSS file named `styles.css` in the `static` directory.
2. Create a JavaScript file named `scripts.js` in the `static` directory.
3. Link the CSS and JavaScript files in your HTML templates:

```html
{% load static %}

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Django Project</title>
    <link rel="stylesheet" href="{% static 'styles.css' %}" />
  </head>
  <body>
    <h1>Welcome to my Django project!</h1>
    <script src="{% static 'script.js' %}"></script>
  </body>
</html>
```

### 8. Create Django Apps

1. Create a Django app by running:

```bash
python manage.py startapp yourappname
```

Replace myapp with the name you want for your app.

2. Add the app to the `INSTALLED_APPS` list in the `settings.py` file.

```python
INSTALLED_APPS = [
    ...
    'yourappname',
]
```
