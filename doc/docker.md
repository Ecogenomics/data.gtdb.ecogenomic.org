# Docker setup

## 1. Generate an SSL certificate

### 1a. Prepare encryption keys

Create the encryption keys required by Certbot:

```shell
mkdir -p /var/www/acme-challenge
wget https://raw.githubusercontent.com/certbot/certbot/master/certbot-nginx/certbot_nginx/_internal/tls_configs/options-ssl-nginx.conf -O /etc/letsencrypt/options-ssl-nginx.conf
openssl dhparam -out /etc/letsencrypt/ssl-dhparams.pem 2048
```

### 1b. Verify certificate

In order for letsencrypt to verify the certificate, NGINX must be able to serve the ACME challenge.

Comment out the second `server` block of the `data_gtdb.conf.template` file and start NGINX:

```shell
docker-compose up -d
```

Now that NGINX is running, verify the certificate:

```shell
certbot certonly --webroot -w /var/www/acme-challenge \
    -d data.gtdb.ecogenomic.org \
    --rsa-key-size 2048 \
    --agree-tos --force-renewal
```

### 1c. Stop the service

After successful validation, stop docker `docker-compose down` and revert the comments 
in the `data_gtdb.conf.template` file: `git stash`

## 2. Start the service

```shell
docker-compose up -d
```

Note: The services will automatically restart even in the event of server restart.
