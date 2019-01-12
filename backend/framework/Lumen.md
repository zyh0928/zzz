## Installation

### Install with Composer

- **Create project**: `composer create-project --prefer-dist laravel/lumen project-name`
- **Run dev server**: `php -S localhost:9028 -t public`

### 前后端分离

- Configure NGINX

  ```nginx
  server {
      listen        80;
      server_name  localhost;

      root .\..\www\picoll\service\public;
      index  index.php  index.html  index.htm;

      location ^~ /api {
        try_files  $uri  $uri/  /index.php?$query_string;
      }

      location / {
          try_files  $uri  $uri/  /index.html;
          alias  ../www/picoll/client/;
      }

      location ~ \.php$ {
          try_files  $uri  /index.php =404;
          fastcgi_split_path_info  ^(.+\.php)(/.+)$;
          fastcgi_pass  127.0.0.1:9000;
          fastcgi_index  index.php;
          fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
          include  fastcgi_params;
      }
  }
  ```

### 设置跨域

- **简单粗暴**：在 **Lumen** 目录下的 /routes/web.php 文件中添加 `header("Access-Control-Allow-Origin:*");`

## Guzzle Http

- **php.ini**: `allow_url_fopen` must be enabled.
- **Install**: `composer require guzzlehttp/guzzle:~6.0`
- **Simple Demo**

  ```php
  # Edit controller file
  use GuzzleHttp\Client;

  public function get(){
    $client = new Client();

    $resp = $client->request('GET', $url);
    # or
    # $resp = $client->get($url);

    $data = $resp->getBody()->getContents();

    return $data;
  }
  ```

## Link

- [**Lumen**](https://lumen.laravel.com/)
