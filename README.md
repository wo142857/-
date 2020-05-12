# Collect

## Redis Utils
### Install
https://www.linode.com/docs/databases/redis/install-and-configure-redis-on-centos-7/


## OpenResty
### Install
sudo yum-config-manager --add-repo https://openresty.org/yum/cn/centos/OpenResty.repo
sudo yum install openresty

## Utils
### 忽略隐藏文件复制
rsync -rv --exclude=.git demo demo_bkp

### lib*.so cannot open shared object file: No such file or directory
```
 find / -name the_name_of_the_file.so
 echo $LD_LIBRARY_PATH
 LD_LIBRARY_PATH=/usr/local/lib
 export LD_LIBRARY_PATH
```

### navicat 破解
https://www.cnblogs.com/wei9593/p/11907307.html

### MySQL 安装
https://juejin.im/post/5d07cf13f265da1bd522cfb6
