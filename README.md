# 如何部署yuanzai bot v3
[目前功能](https://gitee.com/Le-niao/Yunzai-Bot/tree/main/plugins/genshin)
## 准备工作
##### 1.系统Centos7.9
##### 2.有手
##### 3.有大脑
##### 4.有网络
## 开始部署
>环境准备： Node.js（版本至少v16以上），Redis

1.安装Node.js 长期支持版
```
# 下载(没有wget,运行yum install wget -y) 
wget https://npmmirror.com/mirrors/node/v16.18.1/node-v16.18.1-linux-x64.tar.xz
# 解压
tar -xvf node-v16.18.1-linux-x64.tar.xz
# 新建文件夹
mkdir -p /usr/local/nodejs
# 移动
mv node-v16.18.1-linux-x64/* /usr/local/nodejs/
# 建立node软链接
ln -s /usr/local/nodejs/bin/node /usr/local/bin
# 建立npm 软链接
ln -s /usr/local/nodejs/bin/npm /usr/local/bin
# 设置国内镜像源
npm config set registry https://registry.npm.taobao.org
# 查看设置信息
npm config list
#如果显示了node version和npm version就安装成功


```
2.安装Redis
```
# 安装之前必先确认是否安装 gcc 环境（输入gcc -v，如果没有安装，执行以下命令进行安装）
yum install -y gcc 
# 下载Redis
wget ghproxy.com/https://github.com/redis/redis/archive/7.0.8.tar.gz
#解压
tar -zvxf 7.0.8.tar.gz
# 移动
mv redis-7.0.8 /usr/local/redis
#开始安装
cd /usr/local/redis
make
make PREFIX=/usr/local/redis install
# 安装完成

```

3.克隆项目
```
#安装git
yum install git -y

cd /root/

git clone --depth=1 -b main https://gitee.com/Le-niao/Yunzai-Bot.git
```
```
cd Yunzai-Bot #进入Yunzai目录
```
4.安装pnpm，已安装的可以跳过
```
curl -fsSL "ghproxy.com/https://github.com/pnpm/pnpm/releases/latest/download/pnpm-linuxstatic-x64" -o /bin/pnpm; chmod +x /bin/pnpm;
#输入pnpm来检测是否安装成功
```
5.安装依赖
```
pnpm install -P
```
6.运行（首次运行按提示输入登录）
```
node app

#会提示未开启redis服务器,复制命令
cd /usr/local/redis/src
#然后输入打开redis服务器的命令，在前面加上./  没有报错后输入
cd /root/Yuanzai-Bot
node app
#之后就正常流程就行
```
