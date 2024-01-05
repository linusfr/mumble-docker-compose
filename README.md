# Mumble Docker-Compose

Simple docker-compose setup for mumble.
This setup assumes you have certs locally, in this case created by certbot.

# How To

1. Copy the .env.example file to .env

```
cp .env.example .env
```

2. Ensure correct permissions on the .env file

```
chmod 660 .env
```

3. Edit the passwords and the domain in the .env file

4. Start the Service

```
docker compose up -d
```

5. Chown

The service has root permissions initially so that it can retrieve the certificates.
After that it switches to the mumble user.
The mumble user has the UID of 1000.
Most likely it wont have permissions anymore and you need to chown the data dir once.
Also you are most likely UID 1000 yourself.

```
docker compose down
sudo chown -R 1000:docker data
docker compose up -d
```

Now murmur should be coming up properly.

6. Open the Port

Example for ufw

```
sudo ufw allow 64738
```
