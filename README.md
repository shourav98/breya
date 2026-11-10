# Breya

Breya is a Django REST API backend built for a wellness and lifestyle platform focused on nutrition, personal planning, subscriptions, and user engagement. The project combines meal planning, wellness tracking, AI-assisted chat, Google authentication, and premium subscription workflows into a single backend service.

## Overview

This application provides the core API layer for a digital wellness platform with:

- User authentication and onboarding
- Meal and plan management
- Wellness mood tracking and personalized tips
- Live chat and conversational sessions
- Stripe-based subscription flows
- Google OAuth integration
- Firebase push notifications
- Admin dashboard support via Django admin and Unfold

## Tech Stack

- Python 3.11+
- Django 5.2
- Django REST Framework
- PostgreSQL/SQLite-ready configuration
- JWT authentication via `djangorestframework-simplejwt`
- Stripe for subscriptions and checkout
- Google OAuth 2.0
- Firebase Admin SDK
- OpenAI integration
- Django Unfold for admin experience

## Project Structure

```text
breya/
├── api/
│   ├── urls.py
│   └── v1/
│       └── urls.py
├── apps/
│   ├── account/
│   ├── chating/
│   ├── core/
│   ├── meal/
│   ├── myPlans/
│   ├── notifications/
│   ├── subscription/
│   └── wellness/
├── project/
│   ├── conf/
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── media/
├── manage.py
├── requirements.txt
├── firebase_credentials.json
├── db.sqlite3
├── seed_wellness.py
├── verify_final.py
├── test_live_chat.py
└── README.md
```

## Core Features

### Authentication and User Management
- Signup and login APIs
- JWT access and refresh tokens
- Forgot password and OTP verification flow
- Profile management and account deletion
- Google OAuth authentication support

### Meal and Planning
- Meal-related APIs and media support
- Personalized plans and shared plan pages
- Scheduling and planning workflows

### Wellness and Engagement
- Mood tracking
- Wellness situation-based recommendations
- Personalized wellness tips
- AI-assisted conversational workflows

### Subscription Management
- Free and premium plan logic
- Trial activation support
- Stripe checkout and webhook handling
- Plan feature verification and cancellation flow

### Notifications
- Firebase push notification support
- User notification endpoints and services

## Environment Configuration

Create a `.env` file in the project root with the configuration values required by `project/settings.py`.

Example:

```env
SECRET_KEY=your-secret-key
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
CSRF_TRUSTED_ORIGINS=http://localhost,http://127.0.0.1

EMAIL_BACKEND=django.core.mail.backends.console.EmailBackend
EMAIL_HOST=localhost
EMAIL_HOST_USER=
EMAIL_HOST_PASSWORD=
EMAIL_PORT=587
EMAIL_USE_TLS=True

STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
STRIPE_WEBHOOK_SECRET=your_webhook_secret
STRIPE_SUCCESS_URL=http://127.0.0.1:9000/subscription/success/
STRIPE_CANCEL_URL=http://127.0.0.1:9000/subscription/cancel/

OPENAI_API_KEY=your_openai_api_key

GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_REDIRECT_URI=http://127.0.0.1:8000/api/v1/myPlans/google-callback/

FIREBASE_CREDENTIALS_PATH=firebase_credentials.json
MEDIA_FULL_URL=http://127.0.0.1:8000/media/
```

> Note: The project uses `python-decouple` to read environment variables. If a variable is not set, it falls back to sensible defaults defined in the settings.

## Installation

1. Clone the repository:

```bash
git clone https://github.com/shourav98/breya.git
cd breya
```

2. Create and activate a virtual environment:

```bash
python -m venv venv
source venv/bin/activate
# On Windows:
# venv\Scripts\activate
```

3. Install project dependencies:

```bash
pip install -r requirements.txt
```

## Database Setup

Run the migrations:

```bash
python manage.py migrate
```

If needed, create an admin user:

```bash
python manage.py createsuperuser
```

## Running the Server

Start the Django development server:

```bash
python manage.py runserver
```

The app will typically run at:

```text
http://127.0.0.1:8000
```

## API Structure

The project exposes most APIs under the versioned root:

```text
/api/v1/
```

Main modules include:

- `/api/v1/account/` — signup, login, profile, password reset
- `/api/v1/subscription/` — plan access, trial, Stripe checkout, cancellation
- `/api/v1/myPlans/` — plan management and sharing
- `/api/v1/chating/` — live chat and session APIs
- `/api/v1/wellness/` — mood logs and wellness recommendations
- `/api/v1/notifications/` — notifications and user alerts

## Useful Commands

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py test
python manage.py shell
```

## Notes

- The project is configured to use SQLite by default in `project/conf/database.py` for local development.
- Media files are stored under the `media/` directory.
- Firebase credentials should be kept secure and never committed to public repositories unless intentionally meant to be public.

## License

This project is currently maintained for the Breya platform and is intended for the project owner and contributors unless otherwise specified.

## Maintainer

- Shourav
- GitHub: https://github.com/shourav98
