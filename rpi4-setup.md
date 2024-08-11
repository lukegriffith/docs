

# docker

https://www.simplilearn.com/tutorials/docker-tutorial/raspberry-pi-docker

```
cat /etc/os-release
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker lukegriffith
```


# scrypted

https://github.com/koush/scrypted/blob/main/README.md#installation

```
docker run \
  -d --restart unless-stopped \
  --name watchtower \
  -v /var/run/docker.sock:/var/run/docker.sock \
  containrrr/watchtower \
  --interval 3600 --cleanup

```


```
# pull the image
docker pull koush/scrypted
# run the image, saving the database and configuration files in a subdirectory named "scrypted"
docker run \
  --network host \
  -d --restart unless-stopped \
  --name scrypted \
  -v ~/.scrypted/volume:/server/volume \
  koush/scrypted

```
