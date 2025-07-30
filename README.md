<p align="center">
  <a href="https://laravel.com" target="_blank">
    <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo">
  </a>
</p>

<p align="center">
  <a href="https://github.com/laravel/framework/actions">
    <img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status">
  </a>
  <a href="https://packagist.org/packages/laravel/framework">
    <img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads">
  </a>
  <a href="https://packagist.org/packages/laravel/framework">
    <img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version">
  </a>
  <a href="https://packagist.org/packages/laravel/framework">
    <img src="https://img.shields.io/packagist/l/laravel/framework" alt="License">
  </a>
</p>

---

## 📚 Laravel Book Review Project

A Laravel application to manage books and their reviews using MVC, Eloquent relationships, local scopes, aggregation, seeding, caching, and more.

### 🛠️ Setup & Features

- Create project:  
  `composer create-project laravel/laravel book-review`

- Configure database:  
  Edit `.env` and set `DB_DATABASE`, `DB_USERNAME`, and `DB_PASSWORD`.

- Create models & migrate:
  - Create `Book` and `Review` models.
  - Add necessary columns to migration files.
  - Run `php artisan migrate`

- Setup relationships:
  - Add foreign key in migration.
  - Use `hasMany()` and `belongsTo()` in models.

- Seed data:
  - Create factories and seeders.
  - Run `php artisan migrate:refresh --seed`

- Add a local scope:
  - Define `scopeTitle()` in `Book` model to filter by title.
  - View raw SQL using `toSql()` instead of `get()`.

- Use aggregations:
  - `withCount('reviews')`
  - `withAvg('reviews', 'rating')`
  - `reviews()->latest()->limit(3)`
  - Example: top-rated books with more than 10 reviews:
    ```php
    \App\Models\Book::withCount('reviews')
      ->withAvg('reviews', 'rating')
      ->having('reviews_count', '>=', 10)
      ->orderBy('reviews_avg_rating', 'desc')
      ->limit(10)
      ->get();
    ```

- Implement MVC:
  - `php artisan make:controller BookController --resource`
  - `Route::resource('books', BookController::class);`

- Views:
  - Create `layouts/app.blade.php`
  - Create `books/index.blade.php`
  - Return view from controller

- Filtering:
  - Use local scopes in model
  - Apply filters in controller with arrays

- Detail View:
  - Use `load()` for eager loading reviews

- Caching:
  - Cache book list or aggregates
  - Use `booted()` in model to clear cache on change

- Ratings fix:
  - Use `Book::with()` if using `int $id` instead of `Book $book`

- Add reviews:
  - Create `ReviewController`
  - New Blade view for submitting reviews

---

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing)
- [Powerful dependency injection container](https://laravel.com/docs/container)
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent)
- Database agnostic [schema migrations](https://laravel.com/docs/migrations)
- [Robust background job processing](https://laravel.com/docs/queues)
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting)

---

## Learning Laravel

- [Official Docs](https://laravel.com/docs)
- [Laravel Bootcamp](https://bootcamp.laravel.com)
- [Laracasts](https://laracasts.com)

---

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the [Laravel Partners program](https://partners.laravel.com).

### Premium Partners

- **[Vehikl](https://vehikl.com)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel)**
- **[DevSquad](https://devsquad.com/hire-laravel-developers)**
- **[Redberry](https://redberry.international/laravel-development)**
- **[Active Logic](https://activelogic.com)**

---

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

---

## Code of Conduct

Please review the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

---

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

---

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
