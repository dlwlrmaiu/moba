# moba
A Node.js (Express.js) + Vue.js (Element UI)  Moba Project

## 购买域名和服务器

* 服务器有一个公网IP，搭好网站想要访问，需要这个公网IP；域名想要访问这个服务器，也要把域名解析到公网IP
* 连接远程服务器：ssh root@45.65.220.255 第一次连接服务器需要在网页上用远程连接登录

## 域名解析

域名是网站的别名，真正访问的是某一个IP的服务器
域名解析，让域名指向服务器，选择公网IP，让域名等同于该IP，都能访问网站

## Nginx服务器

想要在服务器上搭建一个网站的时候，需要一个web服务器，Nginx就是其中之一

* apt show nginx 
* apt update

运行上面的命令就会有nginx
然后安装nginx  apt install nginx -y
* 操作系统为Ubuntu使用apt，操作系统为CentOs使用yarn

安装好nginx之后就可以通过公网IP或者域名访问，但是此时页面只是nginx的默认页面

## 安装MongoDB数据库

* apt show mongodb 查看MongoDB数据库，是客户端
* apt show mongodb-server 这是服务端

* apt install -y mongodb-server 安装数据库

## git安装、配置ssh-key

* apt install -y git 安装git，然后配置ssh-key

* 配置ssh-key：在本地把代码传到git上面，在服务器上也配置一个key，让服务器可以拉这个代码
    
    * ssh-keygen 之后一路回车生成一个key，然后把这个key复制下来放到线上
    * 该key是一个public key（公钥）
    * cat /root/.ssh/id_rsa.pub 显示公钥内容，然后把其复制下来粘贴到git服务器中配置公钥的地方
    
## 安装node.js，配置淘宝镜像

* apt install -y nodejs

## 拉取代码，安装pm2并启动项目

* 拉取代码：把本地的代码提交到服务器上，在服务器上拉取提交的代码，然后在服务器上有pm2启动node.js的项目，之后就可以访问了
* npm i -g pm2 全局安装pm2，在服务器上部署用pm2，在本地用nodemon
* pm2 start index.js 安装好pm2之后，启动server文件夹里的index.js，并且不占用终端，这样node.js的服务端就启动起来了
* 接下来就是怎样使网站被外网访问，也就是把localhost:3000绑定到nginx上，让公网可以访问

## 配置nginx服务器（配置nginx的反向代理）

* 正向代理：客户端通过某一个服务器（nginx）作为我的代理去访问别人的网站
* 反向代理：在服务器上，nginx本身并不是对外提供服务的，在nginx背后还有一个服务，也就是node.js服务，当我们访问nginx时，nginx就会去找node.js那个服务来提供服务

## 迁移本地数据到服务器（mongodump）

## 使用SSL证书和启用HTTPS安全连接

* http不安全是指传输不安全，https在数据传输之前会被加密，之后再传出去，被人就算获取了也破解不了，但是服务器
* 使网站安全最关键的是需要启动https，而启动https最核心的是要有一个SSL的证书

比较好的开源的SSL证书：let's encrypt

## 使用阿里云oss云存储存放上传文件
