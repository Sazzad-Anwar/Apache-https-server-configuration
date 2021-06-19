<p align="center">
  <img src="./apache_logo.svg"
</p>

<h1 align="center">Apache Https Server Configuration</h1>

### To point the `https` of node application in a LAMP stack server add the below code in `.htaccess` file in application's root directory

```php
RewriteOptions inherit
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

# php -- BEGIN cPanel-generated handler, do not edit
# Set the “ea-php73” package as the default “PHP” programming language.
<IfModule mime_module>
  AddHandler application/x-httpd-ea-php73 .php .php7 .phtml
</IfModule>
# php -- END cPanel-generated handler, do not edit
```

### You can copy the code or download the file of `.htaccess` and include into your application
