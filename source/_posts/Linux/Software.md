---
title: Linux 软件安装
tags:
  - Tag
categories:
  - Linux
--- 

# Linux安装Nginx

## RHEL系YUM安装
This section applies to Red Hat Enterprise Linux and its derivatives such as CentOS, Oracle Linux, Rocky Linux, AlmaLinux.

### 先安装yum工具
```
sudo yum install yum-utils
```
### 在/etc/yum.repos.d/nginx.repo文件中添加以下信息
```
[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key
module_hotfixes=true
```
### 运行以下命令安装nginx
```
sudo yum install nginx
```
