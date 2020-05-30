# Homelab

## Pre-Reqs

Go to the `documentation` directory and use it to pre-configure the server

## Config

### Rclone

Get a configuration file for rclone that looks like this and pit it in `config/`:
```
[gdrive]
type = drive
scope = drive
token = {"access_token":"aaaaaaaaa","token_type":"Bearer","refresh_token":"aaaaaaaaaa","expiry":"2020-05-30T00:04:59.843459857Z"}
root_folder_id = aaaaaaaaaaa
```

### Pi Hole

Pi Hole requires a password in the environment variables of `homelab.yml`


## Deployment

```
docker-compose -f homelab.yml up -d
```

