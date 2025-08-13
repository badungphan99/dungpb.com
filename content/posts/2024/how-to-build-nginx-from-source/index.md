---
author: Phan Bá Dũng
date: '2024-03-29'
summary: >-
  example for build nginx from source
tags: 
  - nginx
title: How to build nginx from source
draft: true
---

Installing some necessary packages

```sh
sudo apt install -y gcc libpcre3-dev libpcre3 libpcre3-dev zlib1g zlib1g-dev libssl-dev libxslt-dev libgd-dev make libgeoip-dev unzip build-essential autoconf automake libtool libcurl4-openssl-dev liblua5.3-dev libpcre2-dev libfuzzy-dev ssdeep gettext pkg-config libpcre3 libpcre3-dev libxml2 libxml2-dev libcurl4 libgeoip-dev libyajl-dev git
```

Download source code then unzip
```sh
wget https://nginx.org/download/nginx-1.24.0.tar.gz
unzip nginx-1.24.0.zip
```

(Optional) for easy monitor your nginx unit
```sh
wget https://github.com/vozlt/nginx-module-vts/archive/refs/tags/v0.2.2.zip
unzip v0.2.2.zip
```

(Optional) for prune cache from nginx
git clone https://github.com/badungphan99/ngx_cache_purge

cd nginx-1.24.0

./configure --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-KTLRnK/nginx-1.24.0=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Wdate-time -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' --prefix=/usr/share/nginx --sbin-path=/usr/sbin/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --modules-path=/usr/lib/nginx/modules --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-compat --with-pcre-jit --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_geoip_module --with-http_auth_request_module --with-http_v2_module --with-http_dav_module --with-http_slice_module --with-threads --with-http_addition_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_image_filter_module=dynamic --with-http_sub_module --with-http_xslt_module=dynamic --with-stream=dynamic --with-stream_ssl_module --with-mail=dynamic --with-mail_ssl_module --add-module=/home/dungpb/nginx-module-vts-0.2.2 --add-module=/home/dungpb/ngx_cache_purge --add-module=/home/dungpb/ngx_http_geoip2_module-3.4

