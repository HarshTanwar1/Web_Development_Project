<div align="center">

# 🛡️ Django Admin Dashboard

A full-featured admin panel built with Django & AdminLTE 3

Custom authentication · Role-based access control · A dynamic no-code CRUD generator

<br>

![Python](https://img.shields.io/badge/Python-3.9-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-3.2-092E20?style=for-the-badge&logo=django&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-3-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Bootstrap](https://img.shields.io/badge/AdminLTE-3-007BFF?style=for-the-badge&logo=bootstrap&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-Data-150458?style=for-the-badge&logo=pandas&logoColor=white)

</div>

<br>

## 📖 Overview

A production-style **admin dashboard** built on the Django web framework and the AdminLTE 3
theme. Beyond standard CRUD, it ships a **custom user model**, **email-verified registration**,
**role-based module permissions**, and a **dynamic CRUD generator** that lets administrators
create, edit, and manage SQLite tables directly from the browser — no code required.

> Built end-to-end during an internship to master Django: authentication, the ORM, templating,
> transactional email, and dynamic database operations

<br>

## ✨ Key Highlights

- 🔐 **Custom Auth System** — email-verified sign-up, secure one-time tokens, password reset & change.
- 👥 **Role-Based Access Control** — per-module permissions assignable to custom roles.
- ⚙️ **No-Code CRUD Generator** — create/drop tables & manage records straight from the UI.
- 📧 **Async Email Delivery** — SMTP email sent on a background thread for fast responses.
- 🎨 **Polished UI** — AdminLTE 3 dashboards, widgets, calendar & gallery.
- 📊 **Audit & Export** — activity logging and one-click database export to CSV.

<br>

## 🧰 Tech Stack

| Layer        | Technologies                                                                  |
| ------------ | ----------------------------------------------------------------------------- |
| **Backend**  | Python 3.9, Django 3.2 (MVT architecture)                                     |
| **Frontend** | AdminLTE 3, Bootstrap, HTML, CSS, JavaScript, Django Template Language        |
| **Database** | SQLite 3 (via the ORM **and** direct `sqlite3` access for the CRUD generator) |
| **Data**     | pandas (CSV import/export & database export)                                  |
| **Email**    | SMTP (Gmail) with Python `threading` for non-blocking delivery                |
| **Auth**     | Django custom user model, `PasswordResetTokenGenerator`, `six`                |

<br>

## 🚀 Features & Functionality

<details open>
<summary><strong>🔐 Authentication & Accounts</strong></summary>

- **Custom user model** (`MyUser`) via `AbstractBaseUser` + `PermissionsMixin` with email, username, role & status.
- **Registration with email verification** — activation link using a base64 UID + signed token.
- **Login / logout** with session handling and a custom password validator.
- **Password reset** by email and **change password** for logged-in users.
- **Superuser / Super Admin** roles with elevated restrictions.

</details>

<details>
<summary><strong>👥 Admin & Role Management</strong></summary>

- Add, edit, delete and **filter** admin users.
- Create, edit and delete **roles**, assigning per-module access (profile, admin, roles, log, settings, CRUD, status, export).
- **Module-level access control** so each role only sees what it's allowed to.

</details>

<details>
<summary><strong>⚙️ Dynamic CRUD Generator</strong></summary>

- **Create and drop** SQLite tables from the web interface.
- **Insert, edit and delete** records — single row, all rows, or the whole table.
- **Live editing** of table structure with changes saved back to the database.

</details>

<details>
<summary><strong>🛠️ Configurable Settings</strong></summary>

- **General** — application name, logo, favicon, timezone & default language.
- **Email (SMTP)** — sender, host, port, user & password.
- **Google reCAPTCHA** — site key, secret key & language.

</details>

<details>
<summary><strong>📊 Dashboards & Utilities</strong></summary>

- Three **dashboard layouts** showcasing AdminLTE widgets.
- **Activity log** with CSV export.
- **Database export** to CSV.
- Calendar, gallery & widget pages.

</details>

<br>

## ⚡ Getting Started

### 1. Clone & enter the project

```bash
git clone https://github.com/HarshTanwar1/Web_Development_Project.git
cd Web_Development_Project
```

### 2. Create and activate a virtual environment _(recommended)_

```bash
# macOS / Linux
python3 -m venv venv
source venv/bin/activate

# Windows
python -m venv venv
.\venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install "Django==3.2" django-adminlte3 pandas six
```

### 4. Configure secrets _(recommended)_

In [`Internship_Project/Internship_Project/settings.py`](Internship_Project/Internship_Project/settings.py), replace the `SECRET_KEY` and the
`EMAIL_HOST_USER` / `EMAIL_HOST_PASSWORD` values with your own (ideally from environment
variables). Email features (activation, password reset) need valid SMTP credentials.

### 5. Migrate, create an admin & run

```bash
cd Internship_Project
python manage.py migrate
python manage.py createsuperuser   # optional but recommended
python manage.py runserver
```

🎉 Open **http://127.0.0.1:8000/** to reach the login page.

<br>

## 🎓 What I Learned

- **Django fundamentals** — the MVT pattern, URL routing, views and the template language.
- **Custom authentication** — building a custom user model & manager and wiring up `AUTH_USER_MODEL`.
- **Secure tokens** — subclassing `PasswordResetTokenGenerator` and encoding/decoding IDs with `urlsafe_base64`.
- **Email in Django** — SMTP backends, HTML emails via `render_to_string`, and sending on a **background thread**.
- **The ORM & migrations** — designing models and evolving the schema safely.
- **Direct database work** — combining the `sqlite3` module and `pandas` to build a dynamic CRUD tool.
- **Role-based access control** — modeling permissions and gating features per role.
- **File uploads, static/media handling**, and integrating a **third-party theme** into Django.

<br>

## 🔮 Future Improvements

- 🔒 **Security hardening (top priority):** move `SECRET_KEY`, Gmail credentials and `DEBUG` out of `settings.py` into **environment variables**, rotate the exposed credentials, set `DEBUG = False` and configure `ALLOWED_HOSTS`.
- 🧱 Implement real `has_perm` / `has_module_perms` checks (currently always `True`).
- 💉 Use **parameterized queries** and validate table/column names in the CRUD generator to prevent SQL injection.
- 🐘 Switch to a **production database** (PostgreSQL/MySQL) for multi-user use.
- ♻️ Refactor the ~1,280-line `views.py` into smaller modules / class-based views with consistent decorators.
- 🧹 Remove committed artifacts (`__pycache__`, the SQLite DB, generated CSVs) and add a proper `.gitignore`.

<br>

---

<div align="center">

⭐ _If you found this project helpful or interesting, consider giving it a star!_ ⭐

</div>
