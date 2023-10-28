# phpbench

使用 Docker Compose 快速构建 nginx + php 容器

## 如何构建 

1. `git clone https://github.com/4lkaid/phpbench.git`
2. `cd phpbench`
3. `docker compose up -d`

## 配置示例

文件路径 `path/phpbench/html/demo/nginx.conf`

```nginx
server {
  listen       80;
  server_name  demo.test;

  location / {
    root   /usr/share/nginx/html/demo;
    index  index.html index.php;
  }

  location ~ \.php$ {
    root           /var/www/html/demo;
    fastcgi_pass   php:9000;
    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include        fastcgi_params;
  }
}
```