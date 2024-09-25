### Clone
```
git clone https://gitlab.com/my-projects7693331/tulip168/odoo/dockovpn.git
```
### Env
```
sudo cp -i .env.example .env
```
- replace `HOST_ADDR` with your vps ip

### Build
```
docker compose up -d --build
```

### Generate new client
```
docker exec dockovpn ./genclient.sh o > <clien-name>.ovpn
```
then download through url onetime provided `vps-ip:1180`
