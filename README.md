# DockOvpn

DockOvpn is an out of the box dockerized OpenVPN server (without UI) with extremely light container.<br>
We would like to extend our gratitude to the Docker image provided by [🔐DockOvpn](https://github.com/dockovpn/dockovpn). Additionally, we add more ease to use `docker` with `.env`. You keep your credential in `.env`.<br>

**How light is it?** 😎
```
[CPUPerc]: 0.03%
[MemPerc]: 0.03%
[MemUsage]: 1.633MiB
```
### Env
```
sudo cp -i .env.example .env
```
Don't forget to define you vps-ip by replacing `HOST_ADDR` with your vps ip.
### ⚒️ Build
```
docker compose up -d --build
```
### Generate new client
```
docker exec dockovpn bash -c "./genclient.sh"
```
then download through url onetime provided `vps-ip:1180`. It will shutdown `:1180` after being downloaded.
### 📖 Headless Usage
If you want to understand deeper please visit [README.md](https://github.com/dockovpn/dockovpn/blob/master/README.md).
___
Stay tune! 😁