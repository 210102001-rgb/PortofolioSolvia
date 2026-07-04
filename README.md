# Solvia Nova — Portfolio Website

Premium digital solution company website built with PHP Native + TailwindCSS CDN.

## Stack

- **Backend**: PHP 8.1+ Native (no framework)
- **Frontend**: TailwindCSS CDN + AlpineJS CDN
- **Database**: MySQL 5.7+
- **Server**: Apache (XAMPP / Rumahweb shared hosting)

---

## Setup Lokal (XAMPP)

### 1. Clone / Copy ke htdocs

```
c:\xampp\htdocs\Portofolio Solvia\
```

### 2. Buat Database

Buka phpMyAdmin → Import file:
```
database/solvianova_db.sql
```

Atau via CLI:
```bash
mysql -u root -p < database/solvianova_db.sql
```

### 3. Konfigurasi

Edit `app/config/config.php`:

```php
define('APP_URL', 'http://localhost/Portofolio Solvia/public');
define('DB_HOST', 'localhost');
define('DB_NAME', 'solvianova_db');
define('DB_USER', 'root');
define('DB_PASS', '');
```

### 4. Akses Website

- **Public**: `http://localhost/Portofolio_Solvia/public`
- **Admin**: `http://localhost/Portofolio_Solvia/public/sso`

### 5. Login Admin Default

```
Username: admin
Password: password
```

> **Ganti password segera** setelah login pertama via Settings.

---

## Struktur Folder

```
/
├── app/
│   ├── config/         # Konfigurasi app & database
│   ├── controllers/    # Controller (MVC)
│   ├── core/           # App, Router, Controller, Model, Database
│   ├── helpers/        # Helper functions
│   ├── models/         # Model (ORM sederhana)
│   ├── routes/         # web.php — semua route
│   └── views/          # Views (PHP templates)
│       ├── admin/      # Admin dashboard views
│       ├── components/ # Navbar, Footer
│       ├── errors/     # 404, dll
│       ├── home/       # Public pages
│       ├── layouts/    # main.php, admin.php
│       ├── portfolio/  # Portfolio views
│       ├── articles/   # Article views
│       └── gallery/    # Gallery view
├── database/
│   └── solvianova_db.sql
└── public/             # Document root
    ├── .htaccess
    ├── index.php
    └── assets/
        ├── css/app.css
        ├── js/app.js
        ├── images/
        └── uploads/    # User uploaded files
```

---

## Deploy ke Rumahweb Shared Hosting

### 1. Upload Files

Upload semua file ke `public_html/` (atau subdomain folder).

### 2. Update Config

```php
define('APP_ENV', 'production');
define('APP_URL', 'https://solvianova.com');
define('DB_HOST', 'localhost');
define('DB_NAME', 'nama_db_hosting');
define('DB_USER', 'user_db_hosting');
define('DB_PASS', 'password_db_hosting');
```

### 3. Import Database

Via phpMyAdmin di cPanel hosting.

### 4. Permissions

```bash
chmod 755 public/assets/uploads/
chmod 755 public/assets/uploads/portfolio/
chmod 755 public/assets/uploads/gallery/
chmod 755 public/assets/uploads/team/
chmod 755 public/assets/uploads/articles/
chmod 755 public/assets/uploads/testimonials/
```

### 5. Aktifkan HTTPS

Uncomment di `public/.htaccess`:
```apache
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

---

## Admin Routes

| Route | Deskripsi |
|-------|-----------|
| `/sso` | Login admin |
| `/sso/dashboard` | Dashboard |
| `/sso/portfolio` | Kelola portfolio |
| `/sso/services` | Kelola services |
| `/sso/gallery` | Kelola gallery |
| `/sso/team` | Kelola tim |
| `/sso/articles` | Kelola artikel |
| `/sso/testimonials` | Kelola testimonial |
| `/sso/messages` | Pesan masuk |
| `/sso/seo` | SEO settings |
| `/sso/settings` | General settings |

---

## SEO Features

- Dynamic meta title & description
- Open Graph & Twitter Card
- Canonical URL
- Auto sitemap.xml → `/sitemap.xml`
- Auto robots.txt → `/robots.txt`
- Schema markup (Organization)
- Lazy image loading
- Clean URL slugs

---

## Catatan Penting

- Tidak memerlukan Node.js di server (TailwindCSS via CDN)
- Tidak memerlukan Composer (pure PHP)
- Compatible dengan PHP 8.0+
- Tested di XAMPP & Rumahweb shared hosting
