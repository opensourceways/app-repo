包下载：wget -O fancyindex.zip https://github.com/aperezdc/ngx-fancyindex/archive/v0.4.3.zip
        tar -xvf fancyindex.zip
编译：cd nginx-1.20.0
      ./configure --prefix=/usr/local/nginx --add-module=../ngx-fancyindex-0.4.3/
1、将此文件夹放在主机的主目录下
2、nginx.conf的某个目录下加上fancyindex配置：
    fancyindex on;
    fancyindex_localtime on;
    fancyindex_exact_size off;
    fancyindex_header "/fancyParam/html/header.html";
    fancyindex_footer "/fancyParam/html/footer.html";
    fancyindex_ignore "fancyParam";
备注：配置时拉会议对齐