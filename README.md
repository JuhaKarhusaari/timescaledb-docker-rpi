### Create docker image
- In dockerfile directory run:
```sh
docker build -t timescaledb .
```
- command belove create image 'timescaledb' 
### Create & start container
**Run this before creating systemd service**
```sh
docker run -d --name timescaledb-server -p 5432:5432 timescaledb
```
- Check that everything is ok and container running
```sh
docker ps
```
- then stop container 
```sh
docker stop timescaledb-server
```
### Create systemd timescaledb.service (autostart)
- Create timescaledb.service file into /lib/systemd/system/
- then run following commands
```sh
sudo systemctl daemon-reload
sudo systemctl enable timescaledb.service
sudo systemctl start timescaledb.service
```
- Now we can check that service & container is running
```sh
## Service check
sudo systemctl status timescaledb.service
```
```sh
## Container check
docker ps
```
- Now we can reboot system and autostart should be working
```sh
sudo reboot
```
- After boot you can run service & container checks to be sure everything is ok.
