---
title:  Centos7-Docker-Install
date: 2021-06-14 10:05:00
tags:
---

## Centos7安装docker
//Another app is currently holding the yum lock; waiting for it to exit  
rm -f /var/run/yum.pid

yum remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine

yum install -y yum-utils device-mapper-persistent-data lvm2

yum-config-manager --add-repo http://download.docker.com/linux/centos/docker-ce.repo

yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

yum list docker-ce --showduplicates | sort -r

yum install -y docker-ce docker-ce-cli

systemctl start docker

systemctl enable docker

docker version

mkdir -p /etc/docker

sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://yqre8ban.mirror.aliyuncs.com"]
}
EOF

systemctl daemon-reload

systemctl restart docker 
