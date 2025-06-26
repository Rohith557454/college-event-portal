# College Events Portal

A web application for managing college events, registrations, and admin approvals. Built with Flask, MySQL, and Bootstrap.

## Features

- User registration and login
- Admin and user roles
- Event creation, listing, and registration
- Admin dashboard with event/request status
- Event approval workflow
- Image upload for events
- Responsive UI with Bootstrap

## Project Structure

```
.
├── app.py
├── config.py
├── create_admin.py
├── requirements.txt
├── run.py
├── schema.sql
├── README.md
├── routes/
│   ├── admin_routes.py
│   ├── auth_routes.py
│   ├── event_routes.py
│   ├── main_routes.py
│   └── __pycache__/
├── templates/
│   ├── base.html
│   ├── events/
│   │   └── list.html
│   ├── main/
│   │   ├── event_details.html
│   │   ├── index.html
│   │   ├── my_registrations.html
│   │   ├── my_requests.html
│   │   └── request_event.html
│   ├── admin/
│   │   ├── dashboard.html
│   │   ├── events.html
│   │   ├── registrations.html
│   │   └── requests.html
│   └── auth/
│       ├── login.html
│       └── register.html
├── static/
│   ├── style.css
│   ├── images/
│   │   ├── college event.jpg
│   │   ├── event1.jpg
│   │   └── event2.jpg
│   └── uploads/
│       ├── 20250601_225753_slide2.jpg
│       ├── 20250602_000259_sudarshan-poojary-AXEdzJLn7DA-unsplash.jpg
│       ├── 20250602_000504_pexels-vishal-panchal-530110781-18597658.jpg
│       ├── 20250602_120412_formation_day.jpg
│       ├── 20250602_120636_formation_day.jpg
│       ├── 20250602_121152_formation_day.jpg
│       ├── 20250602_225645_upscalemedia-transformed.jpeg
│       ├── 20250603_011503_818e9098-1057-4179-afc5-26161bd27e76.jpg
│       ├── 20250603_011544_818e9098-1057-4179-afc5-26161bd27e76.jpg
│       ├── 20250604_001029_WhatsApp_Image_2025-06-04_at_12.07.35_AM.jpeg
│       ├── 20250611_093151_WhatsApp_Image_2025-06-11_at_9.29.22_AM.jpeg
│       ├── 20250611_110110_cricket.jpg
│       └── ... (other uploaded images)
├── .dist/
├── __pycache__/
│   ├── app.cpython-312.pyc
│   └── config.cpython-312.pyc
```

## Setup Instructions

### 1. Clone the repository

```bash
git clone <repo-url>
cd events-portal
```

### 2. Install dependencies

It's recommended to use a virtual environment:

```bash
python -m venv venv
On Windows: venv\Scripts\activate    # On Linux source venv/bin/activate
pip install -r requirements.txt
```

### 3. Configure the database

- Make sure you have MySQL installed and running.
- Edit `config.py` to set your MySQL username, password, and host if needed.
- Create the database and tables:

```bash
mysql -u root -p < schema.sql
```

### 4. Set up environment variables (optional)

You can use a `.env` file for sensitive config (see `python-dotenv`).

### 5. Run the application

```bash
python app.py
```

The app will be available at [http://localhost:5000](http://localhost:5000).

### 6. Create an admin user

If you need to create an admin user, use:

```bash
python create_admin.py
```

## Database Schema

- **users**: id, username, email, password_hash, role, created_at
- **events**: id, title, description, date, time, location, capacity, image_url, status, created_by, created_at
- **event_registrations**: id, event_id, user_id, registration_date, status
- **event_requests**: id, title, description, proposed_date, proposed_time, location, capacity, requested_by, status, admin_remarks, image_url, created_at

See `schema.sql` for full details.

## Dependencies

- Flask==3.0.0
- Flask-Login==0.6.3
- Flask-MySQLdb==2.0.0
- mysqlclient==2.2.1
- Werkzeug==3.0.1
- python-dotenv==1.0.0
- email-validator==2.1.0
- Pillow==10.1.0
- gunicorn==21.2.0

## Folder Details

- `routes/`: Contains Flask blueprints for authentication, main site, admin, and event management.
- `templates/`: Jinja2 templates for all pages (admin, events, auth, etc.).
- `static/`: CSS, images, and uploaded event images.

## Customization

- Change the `SECRET_KEY` in `config.py` for production.
- Update MySQL credentials as needed.
- Adjust upload folder and max file size in `config.py`.

## License

MIT License (or specify your own). # college-event-portal
