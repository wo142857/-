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

2. cgdb reference

   ```sh
   esc:    切换到代码窗口
   quit/q: 退出cgdb
   break [line_number]：（eg: break 61）在某一行设置断点（在61行设置断点）
   n/next：next命令 
   r/run：run命令 
   c/continue：continue命令 
   k/kill：向GDB发送一个kill命令 
   print [variable]： 打印某个变量的值 
   set args []：设置参数 
   show args：显示参数 
   until：当你厌倦了在一个循环体内单步跟踪时，这个命令可以运行程序直到退出循环体。 
   until [line_number]： 运行至某行，不仅仅用来跳出循环 
   call 函数(参数)：调用程序中可见的函数，并传递“参数”，如：call gdb_test(55)
   ```

   

3. cgdb 调试 nginx_rtmp

   ```sh
   # nginx.conf
   daemon off;
   master_process off;
   worker_processes 1;
   
   cd /usr/local/nglp & cgdb nginx/sbin/nginx
   
   cgdb sbin/nginx
   b ngx_rtmp_publish_filter
   run
   ```

   1. 入口函数