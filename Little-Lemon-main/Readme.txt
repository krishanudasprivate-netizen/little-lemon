LITTLE LEMON RESTAURANT API TESTING GUIDE
==========================================

Welcome to the Little Lemon Restaurant Django Application!
This file contains all the API endpoints and paths available for testing.

SERVER INFORMATION:
------------------
Development Server: http://127.0.0.1:8000/
Admin Panel: http://127.0.0.1:8000/admin/

BEFORE TESTING:
--------------
1. Ensure the Django server is running: python manage.py runserver
2. Database migrations are applied: python manage.py migrate
3. (Optional) Create superuser for admin access: python manage.py createsuperuser

AVAILABLE API ENDPOINTS FOR TESTING:
===================================

1. HOME PAGE
   URL: http://127.0.0.1:8000/
   Method: GET
   Description: Restaurant homepage with welcome content
   Expected Response: HTML page with restaurant introduction

2. ABOUT PAGE
   URL: http://127.0.0.1:8000/about/
   Method: GET
   Description: About page with restaurant information
   Expected Response: HTML page with restaurant story and details

3. MENU PAGE
   URL: http://127.0.0.1:8000/menu/
   Method: GET
   Description: Display all menu items ordered by price
   Expected Response: HTML page showing all menu items from database

4. INDIVIDUAL MENU ITEM
   URL: http://127.0.0.1:8000/menu_item/<id>/
   Method: GET
   Examples: 
   - http://127.0.0.1:8000/menu_item/1/
   - http://127.0.0.1:8000/menu_item/2/
   Description: Display details of a specific menu item
   Expected Response: HTML page with individual menu item details

5. BOOKING PAGE
   URL: http://127.0.0.1:8000/book/
   Method: GET, POST
   Description: Restaurant reservation form
   GET: Display booking form
   POST: Submit booking data
   Form Fields:
   - first_name (required)
   - last_name (required)
   - guest_number (required)
   - comment (optional)
   Expected Response: Booking form page

6. ADMIN PANEL
   URL: http://127.0.0.1:8000/admin/
   Method: GET, POST
   Description: Django admin interface for managing data
   Authentication: Requires superuser credentials
   Features:
   - Manage Menu items
   - View/Edit Bookings
   - User management

DATABASE MODELS AVAILABLE:
=========================

MENU MODEL:
----------
Fields:
- id (auto-generated primary key)
- name (CharField, max 200 characters)
- price (IntegerField)

BOOKING MODEL:
-------------
Fields:
- id (auto-generated primary key)
- first_name (CharField, max 200 characters)
- last_name (CharField, max 200 characters)
- guest_number (IntegerField)
- comment (CharField, max 1000 characters, optional)

TESTING SCENARIOS:
=================

SCENARIO 1: Basic Navigation Testing
- Test all GET endpoints to ensure pages load correctly
- Verify responsive design on different screen sizes

SCENARIO 2: Menu Functionality Testing
- Access menu page: http://127.0.0.1:8000/menu/
- Test individual menu items with different IDs
- Verify menu items are ordered by price

SCENARIO 3: Booking Form Testing
- GET http://127.0.0.1:8000/book/ (display form)
- POST form with valid data
- POST form with invalid data (test validation)
- Verify booking saves to database

SCENARIO 4: Admin Panel Testing (requires superuser)
- Login to admin panel
- Add new menu items
- View submitted bookings
- Test CRUD operations

SCENARIO 5: Error Handling Testing
- Test invalid menu item IDs: http://127.0.0.1:8000/menu_item/999/
- Test non-existent URLs: http://127.0.0.1:8000/invalid-page/

SAMPLE TEST DATA:
================

Menu Items (can be added via admin):
- Name: "Grilled Fish", Price: 25
- Name: "Pasta Marinara", Price: 18
- Name: "Caesar Salad", Price: 12
- Name: "Lemon Dessert", Price: 8

Sample Booking Data:
- First Name: "John"
- Last Name: "Doe"
- Guest Number: 4
- Comment: "Window seat preferred"

STATIC FILES:
============
CSS: http://127.0.0.1:8000/static/css/style.css
Images: http://127.0.0.1:8000/static/img/[filename]

ADDITIONAL TESTING NOTES:
========================
- Ensure DEBUG=True in settings.py for development
- Check browser console for any JavaScript errors
- Test form validation and error messages
- Verify database persistence after server restart
- Test both mobile and desktop views

TROUBLESHOOTING:
===============
- If pages don't load: Check if server is running
- If static files missing: Ensure DEBUG=True or run collectstatic
- If database errors: Run python manage.py migrate
- If admin login fails: Create superuser with createsuperuser command

Happy Testing!
Little Lemon Development Team
