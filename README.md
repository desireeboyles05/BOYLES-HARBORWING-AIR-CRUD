# HarborWing Air CRUD Application

This project is the **continuation of the HarborWing Air Midterm Drill**. The Midterm project creates and populates the `harborwing_air` MySQL database; this project provides a PHP web application so users can work with that database without writing SQL manually.

## Connection to the Midterm Drill

- Uses the existing `harborwing_air` database created for the Midterm Drill.
- Uses the Midterm tables, relationships, foreign-key rules, and synthetic/demo data.
- Does not create a separate or unrelated database.
- If the database schema must be changed, update the Midterm SQL scripts and Workbench EER diagram as required by the assignment.

**Midterm Drill GitHub repository:** `https://github.com/desireeboyles05/HarborWing-Air.git`

Before submitting, replace the placeholder above with the actual URL of your Midterm Drill repository. Make sure the Midterm repository's README also links to this CRUD repository.

## Requirements

- PHP 8.1 or newer
- PHP PDO MySQL extension enabled
- MySQL 8.0.16 or newer
- Apache or another PHP-capable local web server (XAMPP is suitable)

## Installation and Setup

1. Finish the Midterm Drill setup first. Make sure the `harborwing_air` database exists and contains your synthetic/demo dataset.
2. If you already have the Midterm database, **do not rerun the original `schema.sql` without a backup and a clear reason**. The Midterm script contains `DROP DATABASE IF EXISTS harborwing_air`, which can remove and recreate the database.
3. Download or clone this CRUD repository.
4. Copy `config.example.php` and name the copy `config.php`.
5. Open `config.php` and enter your local MySQL connection settings:
   - host: usually `127.0.0.1` or `localhost`
   - port: usually `3306`
   - database: `harborwing_air`
   - username: your MySQL username (often `root` for a default local XAMPP setup)
   - password: your local MySQL password (often blank only if your local MySQL account has no password)
6. Keep `config.php` private. It is excluded from Git; do not commit passwords or secret configuration.
7. Put the project folder inside your web server directory. For XAMPP, this is usually `htdocs`, for example `xampp/htdocs/HarborWing-Air-CRUD`.
8. Start Apache and MySQL from the XAMPP Control Panel.
9. Open `http://localhost/HarborWing-Air-CRUD/` in your browser.

If your database settings differ from the examples, use your actual local MySQL settings. Do not copy someone else's password.

## Application Features

The application provides screens for working with these database records:

- Passengers
- Booking agents
- Reservations
- Payments
- Airports
- Flight schedules
- Flight legs
- Flight costs

It also supports reservation-related tasks:

- Add or remove payment links from a reservation.
- Add or remove flight-leg links from a reservation.
- View a reservation with related information.
- Search or filter records.
- View calendar and supporting reference records.

Removing a payment or flight-leg link removes the relationship, not the payment or flight-leg record itself. Calendar/reference data is presented for viewing; the assignment allows these records to be maintained through the Midterm seed script rather than full CRUD screens.

## Demonstration Workflow

Use synthetic/demo records for the class demonstration:

1. Create a passenger.
2. Create a reservation for that passenger.
3. Add two flight legs to the reservation.
4. Create a payment and link it to the reservation.
5. Open the reservation details and show its related information.
6. Update a record.
7. Remove a payment or flight-leg link, then verify the linked record still exists.
8. Delete a record that is eligible for deletion.
9. Attempt an invalid or duplicate operation and show the application's error message.

## How an Application Action Reaches MySQL

For example, when a user submits a passenger form, the application receives the form values, validates the submitted data, and uses PHP PDO prepared statements to send the permitted query and values to MySQL. MySQL checks its primary keys, unique constraints, check constraints, and foreign keys. The application then displays a success message or a readable error.

Prepared statements help prevent SQL injection. Foreign-key constraints help preserve the relationships created in the Midterm database. Operations that affect multiple related records should be handled safely so partial changes are not left behind.

## Troubleshooting

- **Database connection error:** Check that MySQL is running and that the host, port, database name, username, and password in `config.php` are correct.
- **Unknown database:** Complete the Midterm database setup first and confirm the database is named `harborwing_air`.
- **Missing table or column:** Check that the CRUD application is connected to the correct Midterm database version. Do not create a separate database to work around the mismatch.
- **Access denied:** Confirm the MySQL username and password. Do not assume every MySQL installation uses a blank password.

## Security and Data

- Use synthetic/demo data only.
- Do not commit `config.php`, passwords, or other secrets.
- This is a local academic demonstration application, not a production airline booking system.
