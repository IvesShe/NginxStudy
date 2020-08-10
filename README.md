# Nginx Study
學習之後，製作成筆記，方便日後使用時復習

# 在Linux 安裝 Nginx
# 下載Nginx安裝包
版本1.12.2
- [nginx下載](http://nginx.org/en/download.html)

 ![image](./images/20200810195819.png)

# 下載並安裝pcre依賴
```shell
wget http://downloads.sourceforge.net/project/pcre/pcre/8.37/pcre-8.37.tar.gz
```

 ![image](./images/20200810200321.png)

解壓縮
```shell
mv pcre-8.37.tar.gz  /usr/src
cd /usr/src
tar -xvf pcre-8.37.tar.gz
```

 ![image](./images/20200810200647.png)

安裝pcre依賴
```shell
cd pcre-8.37
./configure
```
 ![image](./images/20200810200954.png)

```shell
make && make install
```
![image](./images/20200810201607.png)


查看版本號
```shell
pcre-config --version
```
![image](./images/20200810201848.png)

# 安裝其它的依賴

```shell
yum -y install make zlib zlib-devel gcc-c++ libtool openssl openssl-devel
```
![image](./images/20200810202224.png)
![image](./images/20200810202319.png)

# 安裝Nginx

上傳至linux主機
![image](./images/20200810202632.png)

解壓縮
```shell
tar -xvf nginx-1.12.2.tar.gz
```
![image](./images/20200810202805.png)


```shell
./configure
```
![image](./images/20200810203004.png)
![image](./images/20200810203021.png)

安裝
```shell
make && make install
```
![image](./images/20200810203236.png)
![image](./images/20200810203249.png)

啟動並查看
```shell
cd /usr/local/nginx/sbin/
./nginx 
ps -ef | grep nginx
```
![image](./images/20200810203623.png)

查看設定檔
```shell
vim nginx.conf
```
![image](./images/20200810203909.png)


在阿里雲要把80端口安全組配置打開

![image](./images/20200810204539.png)

![image](./images/20200810204324.png)

訪問該主機，看見Nginx的歡迎畫面了
![image](./images/20200810204348.png)

# 防火牆
一般linux主機使用以下指令，阿里雲主機需在網頁設置安全組
## 查看開放的端口號
```shell
firewall-cmd --list-all
```
![image](./images/20200810205820.png)

## 設置開放的端口號
```shell
# firewall-cmd -add-service=http -permanent
sudo firewall-cmd --add-port=80/tcp --permanent
```

## 重啟防火牆
```shell
firewall-cmd --reload
```

![image](./images/20200810205741.png)

# Nginx操作的常用命令
**使用nginx操作命令前提條件，必須進入nginx的目錄**
```shell
cd /usr/local/nginx/sbin
```

![image](./images/20200810212148.png)

## 查看nginx的版本號
```shell
./nginx -v
```
![image](./images/20200810212413.png)

## 啟動nginx
```shell
./nginx
```
![image](./images/20200810212751.png)

## 關閉nginx的
```shell
ps -ef | grep nginx
./nginx -s stop

```
![image](./images/20200810212625.png)

## 重新加載nginx
```shell
./nginx -s reload
```
![image](./images/20200810212930.png)




