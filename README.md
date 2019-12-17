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
