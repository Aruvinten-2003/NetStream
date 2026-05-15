# Net Stream

Net Stream is a Django-based movie streaming web app. It lets users browse published movies, search and filter by genre, view movie details, stream uploaded MP4 files, register or log in, and maintain a personal watchlist.

## Features

- Movie catalog with poster images, descriptions, genres, release dates, and video files.
- Search movies by title and filter movies by genre from the home page.
- Movie detail pages with poster, metadata, description, and watch actions.
- Browser-based video playback for uploaded movie files.
- User registration, login, and logout using Django authentication.
- Authenticated user watchlists with add, view, and remove actions.
- Django admin support for managing movie records.

## Tech Stack

- Python 3.13
- Django 6.0
- SQLite for local development
- Pillow for image uploads
- HTML templates and CSS

## Project Structure

```text
net_stream/
+-- accounts/          # Registration and auth URL wiring
+-- config/            # Django project settings, URLs, ASGI, and WSGI
+-- media/             # Uploaded posters and videos for local development
+-- movies/            # Movie model, views, URLs, and admin configuration
+-- static/            # Static CSS assets
+-- templates/         # Shared, account, movie, and watchlist templates
+-- watchlist/         # Watchlist model and authenticated watchlist views
+-- db.sqlite3         # Local SQLite database
+-- manage.py          # Django management entry point
+-- requirements.txt   # Python dependency list
```

## Setup

1. Clone or open the project folder.

```bash
cd net_stream
```

2. Create and activate a virtual environment.

```bash
python -m venv venv
venv\Scripts\activate
```

3. Install dependencies.

The current `requirements.txt` file is empty, so install the packages used by the existing project:

```bash
pip install Django pillow
```

Optionally update `requirements.txt` afterward:

```bash
pip freeze > requirements.txt
```

4. Apply database migrations.

```bash
python manage.py migrate
```

5. Create an admin user.

```bash
python manage.py createsuperuser
```

6. Run the development server.

```bash
python manage.py runserver
```

Open the app at:

```text
http://127.0.0.1:8000/
```

## Main Routes

| Route | Description |
| --- | --- |
| `/` | Home page with published movies, search, and genre filtering |
| `/admin/` | Django admin |
| `/accounts/register/` | User registration |
| `/accounts/login/` | User login |
| `/accounts/logout/` | User logout |
| `/movies/<movie_id>/` | Movie detail page |
| `/movies/<movie_id>/watch/` | Movie streaming page |
| `/watchlist/` | Current user's watchlist |
| `/watchlist/add/<movie_id>/` | Add a movie to the current user's watchlist |
| `/watchlist/remove/<movie_id>/` | Remove a movie from the current user's watchlist |

## Managing Movies

Movies are managed through the Django admin. Each movie includes:

- Title
- Description
- Genre
- Release date
- Poster image
- Video file
- Published status

Only movies where `is_published` is enabled are shown on public pages.

## Media Files

Uploaded posters are stored in:

```text
media/posters/
```

Uploaded videos are stored in:

```text
media/videos/
```

In development, media files are served by Django when `DEBUG = True`.

## Development Notes

- The project uses SQLite and a development `SECRET_KEY`, so update settings before production use.
- `DEBUG` is currently enabled and `ALLOWED_HOSTS` is empty.
- `requirements.txt` should be populated before sharing or deploying the project.
- Existing sample media and the local SQLite database are included in the project folder.

## Useful Commands

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```
