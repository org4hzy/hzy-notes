# linux-gitlab搭建流程
ubuntu 环境

* docker install
apt install docker

* gitlab install by docker
```s
docker run --detach \
    --hostname 192.168.49.134 \
    --publish 443:443 --publish 80:80 --publish 22:22 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    gitlab/gitlab-ce:latest
```

* gitlab add ssh key
ssh-keygen -t rsa -C "1209364559@qq.com"

* gitlab-runner install by docker
```s
sudo docker run -d --name gitlab-runner --restart always \
  -v /srv/gitlab-runner/config:/etc/gitlab-runner \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:latest

注册runner到gitlab
sudo docker exec -it gitlab-runner gitlab-ci-multi-runner register
```
OR
* gitlab-runner on linux https://docs.gitlab.com/runner/install/linux-manually.html

* portainer by docker
```s
sudo docker run -d -p 9900:9000 --name my-portainer --restart always portainer/portainer
```

* registry by docker
```s
sudo docker run -d -p 9999:5000 -v /opt/registry:/var/lib/registry --restart=always --name registry registry

上传镜像到本地仓库
golang  dotnet	// 先 tag  再push
```

# redis on docker
```s
sudo docker run --name redis-cache --restart=always -p 6379:6379 -v /srv/redis:/data/redis -d server redis-server --appendonly yes
```
