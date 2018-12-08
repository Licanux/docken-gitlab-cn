# 使用Docker搭建gitlab服务器(中文支持)

1. docker 安装

   ```shell
   sudo apt install docker
   sudo systemctl enable docker
   sudo systemctl start docker
   ```

2. 获取汉化gitlab-ce镜像

   ```
   vim get_gitlab.sh
   ```

   在文件中添加如下内容

   ```shell
   sudo docker run --detach \
       --hostname 192.168.2.113 \
       --publish 443:443 \
       --publish 80:80 \
       --publish 22:22 \
       --name gitlab \
       --restart unless-stopped \
       --volume /srv/gitlab/config:/etc/gitlab \
       --volume /srv/gitlab/logs:/var/log/gitlab \
       --volume /srv/gitlab/data:/var/opt/gitlab \
       twang2218/gitlab-ce-zh:latest
   ```

3. 配置gitlab

   ```shell
   # 启动gitlab
   sudo docker start gitlab
   # 重新配置gitlab以使服务器完成部署
   sudo docker exec gitlab gitlab-ctl reconfigure
   ```

4. 完成