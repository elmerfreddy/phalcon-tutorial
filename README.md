# Phalcon Tutorial

Tutorial básico para usar el framework [phalcon](http://docs.phalconphp.com/en/latest/reference/tutorial.html)

# Instalación

## Apache

Creamos el archivo `tutorial.com.bo`:

```console
cd /etc/apache2/sites-available
sudo vim tutorial.com.bo
```

Con el siguiente contenido:

```apache
<IfModule mod_rewrite.c>

   <Directory "/var/www/tutorial">
     RewriteEngine on
     RewriteRule  ^$ public/    [L]
     RewriteRule  (.*) public/$1    [L]
   </Directory>

   <Directory "/var/www/tutorial/public">
     RewriteEngine On
     RewriteCond %{REQUEST_FILENAME} !-d
     RewriteCond %{REQUEST_FILENAME} !-f
     RewriteRule ^(.*)$ index.php?_url=/$1 [QSA,L]
   </Directory>

 </IfModule>
```

Habilitamos el sitio:

```console
sudo a2ensite tutorial.com.bo
sudo service apache2 reload
```

En el navegador visitamos la URL:

http://localhost/tutorial/

Eso es todo.
