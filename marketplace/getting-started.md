**In addition to the package installation, this one-click deploy also**

* Enables the UFW firewall to allow only SSH (port 22, rate limited), HTTP (port 80), and HTTPS (port 443) access.
* Sets the MySQL root password.
* Sets up the debian-sys-maint user in MySQL so the system’s init scripts for MySQL will work without requiring the MySQL root user password.
* Sets the cron required for background tasks.
* Resolves Cloudflare IP addresses.

## Chevereto Server Details

Chevereto will be available at this URL:

`http://your_server_public_ipv4`

This is an Apache HTTP server based provisioning. PHP runs with `mod_php` using `mpm_prefork`. You can run Chevereto under any configuration, check our [documentation](https://chevereto.com/go/docs) for more information.

## Credentials

The database credentials are at the configuration file at `/var/www/html/app/env.php`.

## Extra-steps

* Provide HTTPS.

```sh
certbot --apache -d example.com -d www.example.com
```

* Disable non-HTTPS access.

```sh
ufw delete allow 80/tcp
```

* Secure MySQL.

```sh
mysql_secure_installation
```

## Upgrades

Chevereto can update itself, simply  open `http://your_server_public_ipv4/dashboard` and click "check upgrades" button.
