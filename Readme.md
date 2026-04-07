# 📝 Django Todo App

A full-stack **Todo List Web Application** built using Django that allows users to manage their daily tasks efficiently with authentication and personalized task management.

![Django](https://img.shields.io/badge/Django-5.0-green)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Status](https://img.shields.io/badge/Status-Active-success)

🌐 **Live Demo:**  
https://todo-python-using-django-1.onrender.com

📂 **GitHub Repository:**  
https://github.com/rojanagunoori/todo-python-using-Django

---

## 1️⃣ Project Overview

This project is a **full-stack task management web application** built using Django that enables users to efficiently organize and manage their daily activities in a secure, user-specific environment.

The application provides a complete workflow for task management — from user authentication to task creation, tracking, updating, and deletion — all within an intuitive and clean interface.

Each user has a **personalized dashboard**, ensuring that tasks remain private and isolated, which is a critical feature in multi-user systems.

### 🎯 Purpose

The primary objectives behind building this project include:

- Gaining hands-on experience with **Django framework architecture**
- Understanding and implementing **user authentication & authorization**
- Building a **real-world CRUD (Create, Read, Update, Delete) application**
- Learning how to structure scalable Django projects using **Class-Based Views (CBVs)**
- Implementing **secure data handling practices** such as CSRF protection and user-based filtering
- Exploring **deployment workflows** using platforms like Render
- Strengthening backend development skills with **clean, maintainable code practices**

## 2️⃣ 🚀 Features

This application includes a range of features designed to provide a smooth and efficient task management experience:

### 🔐 Authentication System

- Secure user registration with password validation
- Login and logout functionality using Django’s built-in authentication system
- Session-based authentication to maintain user state
- Protection of routes using `LoginRequiredMixin`

### 📝 Task Management (CRUD Operations)

- Create new tasks with title, description, and completion status
- View all tasks in a structured list format
- Update existing tasks seamlessly
- Delete tasks with confirmation to prevent accidental removal

### ✅ Task Status Tracking

- Mark tasks as **complete or incomplete**
- Visual indicators to differentiate completed vs pending tasks
- Automatic sorting based on completion status

### 🔍 Search Functionality

- Real-time filtering of tasks based on keywords
- Case-insensitive search using Django ORM (`icontains`)
- Improves usability for users with large task lists

### 👤 User-Specific Data Isolation

- Each user can only view and manage their own tasks
- Prevents unauthorized access to other users’ data
- Implemented using query filtering based on logged-in user

### 📊 Task Insights

- Displays count of incomplete tasks
- Provides quick overview of pending work

### 🎨 User Interface

- Clean, minimal, and responsive UI design
- Built using HTML and CSS
- Template inheritance for consistent layout

### 🔒 Security Features

- CSRF protection enabled on all forms
- Secure password handling using Django’s hashing system
- Restricted access to authenticated users only

---

## 3️⃣ Folder / Project Structure

```bash
todo-python-using-Django/
│
├── todolistprj/ # Main Django project
│ ├── settings.py
│ ├── urls.py
│ ├── wsgi.py
│
├── todo/ # Core application
│ ├── models.py # Task model
│ ├── views.py # Business logic (CBVs)
│ ├── urls.py # App routes
│ ├── admin.py
│ ├── templates/
│ │ └── todo/
│ │ ├── main.html
│ │ ├── login.html
│ │ ├── register.html
│ │ ├── task_list.html
│ │ ├── task_form.html
│ │ ├── task_confirm_delete.html
│ │ └── task.html
│
├── db.sqlite3
├── manage.py
├── requirements.txt
├── .env
└── README.md
```

---

## 4️⃣ 🛠️ Tech Stack / Environment

This project utilizes a modern and lightweight tech stack suitable for rapid development and deployment.

### 🧠 Backend

- **Django 5.x**
  - High-level Python web framework
  - Handles routing, ORM, authentication, and business logic

- **Python 3.x**
  - Core programming language

### 🎨 Frontend

- **HTML5**
  - Structure of web pages

- **CSS3**
  - Styling and layout design

### 🗄️ Database

- **SQLite**
  - Default database for development
  - Lightweight and easy to configure

### ☁️ Deployment

- **Render**
  - Cloud platform used to host the application
  - Supports Django deployment with minimal configuration

### 🧰 Tools & Libraries

- **python-dotenv**
  - Manages environment variables securely
  - Keeps sensitive data like SECRET_KEY out of source code

- **WhiteNoise**
  - Serves static files efficiently in production
  - Eliminates need for external static file servers

- **Gunicorn**
  - Production-ready WSGI server
  - Handles incoming HTTP requests efficiently

---

## 5️⃣ ⚙️ Installation / Setup

### 1. Clone Repository

```bash
git clone https://github.com/rojanagunoori/todo-python-using-Django.git
cd todo-python-using-Django
```

### 2. Create Virtual Environment

```bash
python -m venv env
source env/bin/activate      # Linux / Mac
env\Scripts\activate         # Windows
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Run Server

```bash
python manage.py runserver
```

Visit:
http://127.0.0.1:8000/

---

## 6️⃣ 🔐 Environment Variables

Create a .env file in the root directory:

```bash
SECRET_KEY=your_secret_key
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost
```

---

## 7️⃣ 🔌 API Usage

This project primarily uses Django views, but endpoints behave like APIs:

```bash
| Endpoint             | Method   | Description       |
| -------------------- | -------- | ----------------- |
| `/login/`            | GET/POST | User login        |
| `/register/`         | GET/POST | User registration |
| `/`                  | GET      | View all tasks    |
| `/task-create/`      | POST     | Create new task   |
| `/task-update/<id>/` | POST     | Update task       |
| `/task-delete/<id>/` | POST     | Delete task       |
```

---

## 8️⃣ 🧩 Key Components

### 📌 Models

#### Task Model

The core data model of the application representing a task.

**Fields:**

- `user` → ForeignKey to User model (task ownership)
- `title` → Short description of the task
- `description` → Detailed task information (optional)
- `complete` → Boolean field to track status
- `time_created` → Timestamp when task was created

**Key Features:**

- Establishes relationship between user and tasks
- Enables user-specific data filtering
- Supports task status tracking

---

### 📌 Views

The application uses **Django Class-Based Views (CBVs)** for better code organization and reusability.

#### Implemented Views:

- **ListView** → Displays all tasks for the logged-in user
- **DetailView** → Shows detailed view of a single task
- **CreateView** → Handles task creation
- **UpdateView** → Handles task updates
- **DeleteView** → Handles task deletion with confirmation

**Enhancements:**

- Overridden `get_queryset()` to enforce user-based filtering
- Custom `form_valid()` to associate tasks with logged-in users
- Search functionality integrated into ListView

---

### 📌 Templates

The frontend uses Django’s templating engine:

- **Template Inheritance**
  - `main.html` acts as the base layout
  - Other templates extend it for consistency

- **Dynamic Rendering**
  - Uses Django Template Language (DTL)
  - Displays user data, tasks, and conditional UI elements

- **Reusable Components**
  - Header bar
  - Forms
  - Task list layout

---

## 9️⃣ 🔒 Security

Security is a key focus of this application.

### Implemented Measures:

- **Authentication System**
  - Uses Django’s built-in user authentication

- **Authorization**
  - Only authenticated users can access task-related pages

- **CSRF Protection**
  - All forms include CSRF tokens to prevent cross-site request forgery

- **User Data Isolation**
  - Queries are filtered by logged-in user
  - Prevents access to other users’ data

- **Password Security**
  - Passwords are hashed using Django’s secure hashing algorithms

---

## 🔟 ⚠️ Challenges Faced During Development

### 1. User Data Leakage

- **Problem:** Tasks were initially visible across all users
- **Cause:** Queries were not filtered by user
- **Solution:** Implemented user-based filtering using:

  ```python
  Task.objects.filter(user=self.request.user)
  ```

---

### 2. Environment Variables Misconfiguration

- **Problem:** Application failed due to incorrect `.env` format
- **Cause:** Used Python-style variables instead of dotenv format
- **Solution:** Corrected `.env` syntax and used `python-dotenv`

---

### 3. Static Files Not Loading in Production

- **Problem:** CSS not applied after deployment
- **Solution:**
  - Integrated WhiteNoise middleware
  - Configured `STATIC_ROOT` and `STATICFILES_STORAGE`

---

### 4. Authentication Redirect Issues

- **Problem:** Improper redirection after login/logout
- **Solution:**
  - Configured:
    - `LOGIN_REDIRECT_URL`
    - `LOGOUT_REDIRECT_URL`

---

## 1️⃣1️⃣ 🚀 Future Improvements

To further enhance the functionality, scalability, and user experience of the application, the following improvements and features are planned:

---

### 📅 Task Deadlines & Smart Reminders

- Introduce a **due date field** for each task
- Allow users to set **custom deadlines**
- Implement **reminder notifications** before deadlines
- Highlight overdue tasks visually (e.g., red indicators)
- Option to sort/filter tasks by deadline

---

### 🔥 Priority Levels (High, Medium, Low)

- Add a **priority field** to each task
- Use **color-coded indicators** for quick identification
  - 🔴 High Priority
  - 🟡 Medium Priority
  - 🟢 Low Priority

- Enable sorting and filtering based on priority
- Improve task management efficiency for users

---

### 📧 Email Notifications System

- Send automated **email reminders** for:
  - Upcoming deadlines
  - Overdue tasks

- Use Django’s email backend (SMTP integration)
- Optional user preferences:
  - Enable/disable notifications
  - Set reminder frequency

- Can be extended to support **push notifications**

---

### 🌐 REST API Integration (Django REST Framework)

- Build a **RESTful API layer** using Django REST Framework (DRF)
- Enable CRUD operations via API endpoints
- Allow integration with:
  - Mobile applications
  - Third-party services

- Implement authentication using:
  - Token Authentication / JWT

- Improve scalability and extensibility of the project

---

### 🎨 UI/UX Enhancements

- Upgrade UI using modern frameworks like:
  - **Bootstrap** (quick styling)
  - **React.js** (advanced frontend)

- Add:
  - Responsive navigation bar
  - Interactive components (modals, alerts)
  - Better form styling and validation feedback

- Improve overall user experience and accessibility

---

### 📄 Pagination for Task Lists

- Implement pagination for better performance with large datasets
- Limit number of tasks displayed per page
- Add navigation controls (Next, Previous, Page numbers)
- Improve loading speed and usability

---

### 📱 Mobile Responsiveness & Cross-Device Support

- Optimize UI for mobile and tablet devices
- Use responsive design techniques (Flexbox/Grid)
- Ensure compatibility across:
  - Different screen sizes
  - Browsers and devices

- Enhance touch interactions for mobile users

---

### 📊 Analytics Dashboard

- Provide insights into user productivity:
  - Total tasks created
  - Completed vs pending tasks
  - Task completion trends

- Use charts and graphs (e.g., Chart.js)
- Optional features:
  - Weekly/monthly reports
  - Productivity scoring

- Helps users track and improve performance

---

### 🔐 Advanced Security Enhancements

- Implement features like:
  - Two-Factor Authentication (2FA)
  - Email verification during registration

- Add login attempt limits to prevent brute-force attacks
- Improve overall application security

---

### 🧠 Performance Optimization

- Optimize database queries using Django ORM techniques
- Use caching (Redis) for faster responses
- Reduce page load times
- Prepare the app for scaling to multiple users

---

### ☁️ Deployment & DevOps Improvements

- Add Docker support for containerization
- CI/CD pipeline integration (GitHub Actions)
- Use PostgreSQL instead of SQLite for production
- Improve deployment automation

---

These enhancements will transform the application from a basic task manager into a **scalable, production-ready system** with modern features and improved user experience.

---

## 1️⃣2️⃣ 🤝 Contributing

Contributions are welcome!

Steps:

1. Fork the repository
2. Create a new branch (`feature-xyz`)
3. Commit your changes
4. Push to branch
5. Open a Pull Request

---

## 1️⃣3️⃣ 🙏 Acknowledgments

- Django Documentation
- YouTube tutorials
- Open-source community
- Render platform

---

## 1️⃣4️⃣ 📄 License

This project is licensed under the MIT License.

---

## 🙋‍♀️ Author / Contact

**Nagunoori Roja**

- 📧 Email: [nagunooriroja@gmail.com](mailto:nagunooriroja@gmail.com)
- 🌐 GitHub: [https://github.com/rojanagunoori](https://github.com/rojanagunoori)
- 🌐 LinkedIn: [https://www.linkedin.com/in/nagunoori-roja-51b936267/](https://www.linkedin.com/in/nagunoori-roja-51b936267/)
- 🌐 Personal Portfolio: [portfolio-roja.netlify.app](https://portfolio-roja.netlify.app/)
- 🌐 LeetCode: [https://leetcode.com/u/dSdsi6XkI8/](https://leetcode.com/u/dSdsi6XkI8/)
- 🌐 Kaggle: [https://www.kaggle.com/nagunooriroja](https://www.kaggle.com/nagunooriroja)

⭐ If you found this project useful, please give it a star!

---

# 🔥 This README is now:

✔ Industry-level  
✔ Resume-ready  
✔ Recruiter-friendly  
✔ Deployment-ready  
✔ GitHub professional standard

---

If you want next upgrade, I can:

- Add **screenshots section (with styling)**
- Add **GIF demo**
- Add **badges like deploy status**
- Convert this into **portfolio project description**

Just tell 👍
