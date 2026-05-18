# 📚 Library Management System
![Uploading LMS.jpg…]()


A professional, full-stack Library Management System built with Django REST Framework. Manage books and authors with a beautiful, responsive web interface and REST API.

## ✨ Features

- ✅ **REST API** - Full CRUD operations (GET, POST, PUT, DELETE) for books and authors
- ✅ **Professional Dashboard** - Beautiful, responsive web interface with real-time updates
- ✅ **Book Management** - Add, edit, delete, and search books
- ✅ **Author Management** - Manage authors and their books
- ✅ **Availability Tracking** - Mark books as available or borrowed
- ✅ **Statistics** - Real-time dashboard statistics
- ✅ **Admin Panel** - Django admin interface for advanced management
- ✅ **Sample Data** - Optional setup with sample books and authors

## 🚀 Quick Start

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Run Setup Script

```bash
python setup.py
```

This will:
- Run database migrations
- Create a superuser account
- Optionally load sample data

### 3. Start Development Server

```bash
python manage.py runserver
```

The application will be available at:
- 🌐 **Dashboard**: http://localhost:8000/
- 🔐 **Admin**: http://localhost:8000/admin/
- 🔌 **API**: http://localhost:8000/api/

## 📖 API Endpoints

### Books
- `GET /api/books/` - List all books
- `POST /api/books/` - Create a new book
- `GET /api/books/<id>/` - Retrieve a specific book
- `PUT /api/books/<id>/` - Update a book
- `PATCH /api/books/<id>/` - Partial update a book
- `DELETE /api/books/<id>/` - Delete a book
- `GET /api/books/available_books/` - Get only available books
- `POST /api/books/<id>/toggle_availability/` - Toggle book availability

### Authors
- `GET /api/authors/` - List all authors
- `POST /api/authors/` - Create a new author
- `GET /api/authors/<id>/` - Retrieve a specific author
- `PUT /api/authors/<id>/` - Update an author
- `PATCH /api/authors/<id>/` - Partial update an author
- `DELETE /api/authors/<id>/` - Delete an author

## 💻 Dashboard Features

### Add/Edit Book
- Create new books with title, author, ISBN, and publication date
- Edit existing books
- Set availability status

### Quick Add Author
- Add new authors with name and email
- Authors are linked to books

### Books List
- View all books in a table format
- Search by title or ISBN
- Edit or delete books
- Visual availability status badges

### Authors List
- View all authors
- See book count for each author
- Delete authors (cascades to their books)

### Statistics
- Total books count
- Available books count
- Total authors count

## 🛠️ Creating a Superuser Manually

If you skip the setup script or need to create additional superusers:

```bash
python manage.py createsuperuser
```

Or use the custom command:

```bash
python manage.py create_superuser_custom
```

## 📁 Project Structure

```
library_project/
├── books/
│   ├── management/
│   │   └── commands/
│   │       └── create_superuser_custom.py
│   ├── migrations/
│   ├── templates/
│   │   └── books/
│   │       └── index.html
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── serializers.py
│   ├── urls.py
│   ├── views.py
│   └── tests.py
├── library_project/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
├── setup.py
├── manage.py
├── db.sqlite3
└── requirements.txt
```

## 📊 Data Models

### Author
- `id` - Primary key
- `name` - Author's name
- `email` - Author's email (unique)

### Book
- `id` - Primary key
- `title` - Book title
- `author` - Foreign key to Author
- `isbn` - ISBN-13 (unique)
- `published_date` - Date book was published
- `is_available` - Availability status (boolean)

## 🎨 Technology Stack

- **Backend**: Django 6.0.5
- **API**: Django REST Framework 3.14.0
- **Database**: SQLite
- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Styling**: Modern CSS with gradients and animations

## 📝 Example API Usage

### Add a Book (POST)
```json
{
  "title": "The Hobbit",
  "author": 1,
  "isbn": "9780547928227",
  "published_date": "1937-09-21",
  "is_available": true
}
```

### Update a Book (PUT)
```json
{
  "title": "The Hobbit - Revised",
  "author": 1,
  "isbn": "9780547928227",
  "published_date": "1937-09-21",
  "is_available": false
}
```

### Add an Author (POST)
```json
{
  "name": "J.R.R. Tolkien",
  "email": "tolkien@example.com"
}
```

## 🔒 Security Notes

- Change the SECRET_KEY in `settings.py` before production
- Set `DEBUG = False` in production
- Use environment variables for sensitive data
- Set up proper authentication for API in production

## 📚 Troubleshooting

### Database Issues
```bash
# Delete database and start fresh
rm db.sqlite3
python manage.py migrate
python setup.py
```

### Port Already in Use
```bash
# Use a different port
python manage.py runserver 8080
```

### CSRF Token Errors
- Make sure cookies are enabled in your browser
- Refresh the page and try again

## 🤝 Contributing

Feel free to enhance this project with:
- User authentication
- Book reservations
- Due dates for borrowed books
- Email notifications
- Advanced search filters

## 📄 License

This project is open source and available for educational purposes.

---

**Happy Library Managing! 📚✨**
