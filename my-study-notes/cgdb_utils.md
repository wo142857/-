### 利用 cgdb 学习 nginx_rtmp 源码

1. 编译 nginx_rtmp

   ```sh
   git clone http://gitlab.dwion.com/devlive-team/nginx-rtmp-module.git
   
   # 切换至 rpmbuild 分支
   git fetch origin dev-add-rpmbuild
   git checkout -b dev-add-rpmbuild origin/dev-add-rpmbuild
   
   cd nginx-rtmp-module/rpmbuild
   
   # 下载 modules
   python download
   
   # 编译
   cd ./openssl & ./config
   
   cd openresty
   ./configure --prefix=/usr/local/nglp --add-module=../nginx-rtmp-module --add-module=../nginx-client-module --add-module=../nginx-multiport-module --add-module=../nginx-toolkit-module --add-module=../ngx_reset_vhost_module --with-pcre=../pcre --with-openssl=../openssl
   
   make & make install
   
   ```

2. cgdb 调试 nginx_rtmp

   ```sh
   # nginx.conf
   daemon off;
   master_process off;
   worker_processes 1;
   
   cd /usr/local/nglp & cgdb nginx/sbin/nginx
   
   ```

   1. 入口函数