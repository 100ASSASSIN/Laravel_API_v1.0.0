##### API Documentation:


PHP version :

PHP version 8.2.21 (/usr/bin/php8.2)

Composer version :

Composer version 2.7.6 2024-05-04 23:03:15

Laravel version :

Laravel Framework 8.83.27

MYSQL version :

mysql  Ver 8.0.37-0ubuntu0.22.04.3 for Linux on x86_64 ((Ubuntu))


******************

MYSQL Configure: 

FilePath => .env 

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=aus
DB_USERNAME=root
DB_PASSWORD=12345

******

FilePath => API_ENDPOINT/config/database.php

'default' => env('DB_CONNECTION', 'mysql'),

        'mysql' => [
            'driver' => 'mysql',
            'url' => env('DB_URL'),
            'host' => env('DB_HOST', '127.0.0.1'),
            'port' => env('DB_PORT', '3306'),
            'database' => env('DB_DATABASE', 'aus'),
            'username' => env('DB_USERNAME', 'root'),
            'password' => env('DB_PASSWORD', '12345'),
            'unix_socket' => env('DB_SOCKET', ''),
            'charset' => env('DB_CHARSET', 'utf8mb4'),
            'collation' => env('DB_COLLATION', 'utf8mb4_unicode_ci'),
            'prefix' => '',
            'prefix_indexes' => true,
            'strict' => true,
            'engine' => null,
            'options' => extension_loaded('pdo_mysql') ? array_filter([
                PDO::MYSQL_ATTR_SSL_CA => env('MYSQL_ATTR_SSL_CA'),
            ]) : [],
        ],

******************

CLI COMMENDS : 

php artisan migrate
php artisan config:clear
php artisan cache:clear
php artisan route:clear
php artisan view:clear

********************************
Cross-Site Request Forgery (CSRF)

The full form of "CSRF token" is **"Cross-Site Request Forgery Token."**

### Explanation:

- **Cross-Site Request Forgery (CSRF)**: This is a type of attack where a malicious website tricks a user's browser into making unwanted requests to a different website where the user is authenticated. These requests can perform actions on the user's behalf without their consent.

- **Token**: In the context of CSRF, a token is a unique, secret value generated by the server and included in forms or HTTP requests. This token is used to verify that the request originated from a legitimate source (i.e., the same site that generated the token).

### How CSRF Tokens Work:

1. **Generation**: When a user accesses a page that requires a CSRF token, the server generates a unique token and embeds it in the page (usually in hidden form fields or HTTP headers).

2. **Inclusion**: When the user submits a form or makes an HTTP request, the token is included in the request.

3. **Validation**: The server verifies that the token included in the request matches the token stored in the user's session. If the tokens match, the request is processed. If not, the request is rejected.

### Purpose:

The CSRF token is used to protect web applications from CSRF attacks by ensuring that requests made to the server are coming from trusted sources (i.e., the application itself) and not from malicious third-party websites.

In Laravel, CSRF tokens are automatically included in forms generated by the framework, and they are checked on every request to verify authenticity.

**********************************
GET API :

http://127.0.0.1:8000/api/employees

Output:
[
    {
        "id": 1,
        "name": "John Doe",
        "date": "2023-07-22",
        "time": "09:00:00",
        "active_status": 1
    },
    {
        "id": 2,
        "name": "Jane Smith",
        "date": "2023-07-22",
        "time": "09:30:00",
        "active_status": 0
    },
    {
        "id": 3,
        "name": "Alice Johnson",
        "date": "2023-07-23",
        "time": "10:00:00",
        "active_status": 1
    },
    {
        "id": 4,
        "name": "Bob Brown",
        "date": "2023-07-23",
        "time": "10:30:00",
        "active_status": 1
    }
]




PUT API :

http://localhost:8000/api/employees/update?id=1&name=akash&date=2023-07-25&time=10:00:00&active_status=true


http://localhost:8000/api/emp/?id=2&name=bot&date=2023-07-22&time=09:00:00&active_status=1

http://localhost:8000/api/emp/update?id=1&name=akash&date=2023-07-25&time=10:00:00&active_status=true

*****************************************
curl -X PUT "http://localhost:8000/api/employees/1" \
-H "Content-Type: application/json" \
-d '{
    "name": "Updated Name",
    "date": "2023-07-25",
    "time": "10:00:00",
    "active_status": true
}'

