## NorthBrand Restaurant

NorthBrand Restaurant is a PHP & MySQL powered ordering platform for a boutique Sri Lankan restaurant. Customers can browse a visual menu, add dishes to the cart, submit reservations, reviews, and contact requests, while staff manage menus, gallery assets, and incoming orders through an admin dashboard.

---

### Features
- **Dynamic catalog** sourced from MySQL with category filters (All, Fast Foods, Indian Foods, Drinks, Tava).
- **Online ordering flow** with user accounts, cart management, checkout, and order tracking.
- **Rich marketing pages** including About, Gallery, Blog, Contact, Reservation, and Review submission.
- **Admin console** (CRUD for menu items, categories, gallery, and reviews) with session-protected access.
- **Responsive UI** built with Bootstrap, Font Awesome, and custom CSS/JS animations.

---

### Tech Stack
- Frontend: HTML5, Bootstrap 4, custom CSS (`css/style.css`, `css/custom.css`), Vanilla JS/jQuery.
- Backend: PHP 7+, mysqli extension, sessions for auth.
- Database: MySQL (schema provided in `database/North.sql`).
- Assets: Static images under `images/` plus admin-managed uploads in `admin/img/` & `admin/mimg/`.

---

### Project Structure
```
NorthBrand_Restaurent/
├── index.php               # Landing page + featured menu & reviews
├── menu.php, order.php     # Menu listing and order placement views
├── login.php, registration.php, logout.php, loginck.php
├── cart.php, addcart.php, deletecart.php, checkout.php, viewcart.php
├── about.html/.php, blog*.html, gallery*.php, contact*.php, reservation.html
├── admin/                  # Admin dashboard (menu, category, gallery, review CRUD)
├── css/, js/, fonts/, images/
├── database/North.sql      # Sample schema + seed data
└── README.md               # You are here
```

---

### Getting Started
1. **Prerequisites**
   - XAMPP / LAMP stack with PHP 7.4+ and MySQL 5.7+.
   - Composer is optional (no dependencies required).

2. **Project Setup**
   - Place `NorthBrand_Restaurent/` inside your server root (e.g., `htdocs` for XAMPP).
   - Create a MySQL database named `NorthBrand`.
   - Import `database/North.sql` via phpMyAdmin or the MySQL CLI:
     ```bash
     mysql -u root -p NorthBrand < database/North.sql
     ```
   - Update database credentials in `connect.php` and `admin/connect.php` if your environment differs from the default `root` / no password.

3. **Run Locally**
   - Start Apache & MySQL services via XAMPP (or your stack).
   - Visit `http://localhost/NorthBrand_Restaurent/` for the customer site.
   - Visit `http://localhost/NorthBrand_Restaurent/admin/` for the admin portal.
   - Alternatively, run PHP’s built-in server from the project root:
     ```bash
     php -S localhost:8000
     ```

---

### Admin Access
- URL: `http://localhost/NorthBrand_Restaurent/admin/`
- Credentials: `admin` / `admin`

> Change the default password immediately for production deployments. Update `admin/loginck.php` after hashing the new password.

---

### Key Workflows
- **Menu management**: Admin creates categories (`admin/food_cat.php`) and menu items (`admin/food.php`); images are uploaded to `admin/img/`.
- **Orders & cart**: Logged-in users add dishes (`addcart.php`), review their cart (`cart.php`), and confirm at checkout (`checkout.php`).
- **Gallery & reviews**: Admin curates gallery entries (`admin/gallery.php`) and moderates reviews (`admin/review.php` / `admin/delreview.php`).
- **Content pages**: Static marketing sections live under the root (`about.html`, `blog.html`, `stuff.html`, etc.) and can be edited directly.

---

### Database
- Default database name: `NorthBrand`
- Tables include: `menu`, `gallery`, `review`, `category`, `users`, `orders`, `cart`, etc.  
- Re-import `database/North.sql` whenever you need a clean dataset.

---

### Customization Notes
- **Branding**: Replace logos under `images/Logo.png` / `images/NB Logo.png`.
- **Colors & typography**: Adjust `css/style.css` and `css/custom.css`.
- **Email hooks**: Contact & reservation forms post to `php/form-process.php`; plug in SMTP or mail APIs as needed.
- **Security hardening** (recommended for production):
  - Add CSRF tokens to forms.
  - Hash stored passwords (e.g., `password_hash`).
  - Validate & sanitize uploads before saving them under `admin/img/`.

---

### Troubleshooting
- **Blank pages / errors**: Enable PHP errors in `php.ini` (`display_errors=On`) or add `ini_set('display_errors', 1);` in `index.php` temporarily.
- **Database connection failures**: Confirm hostname, credentials, and that the `NorthBrand` database exists; test via `mysqli_connect_error()`.
- **Missing assets**: Ensure directories under `admin/img/` and `admin/mimg/` are readable by Apache; set correct permissions on Linux (`chmod -R 755`).

---

### License
This project is provided as-is for learning/demo purposes. Adapt, extend, or rebrand it to suit your deployment needs.


