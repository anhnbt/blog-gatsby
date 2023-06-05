# Blog AnhNBT.

Đây là nơi lưu trữ và chia sẻ mã nguồn trang blog của mình: [**Demo**](https://blog.anhnbt.com)

## Hướng dẫn cài đặt

Clone project: https://github.com/anhnbt/blog

Install thư viện:

```shell
npm i
```

Cài đặt Gatsby CLI: https://www.gatsbyjs.com/docs/tutorial/part-0/#gatsby-cli

```shell
npm install -g gatsby-cli
```

Kiểm tra version

```shell
gatsby --version
```

## Chạy dự án trên localhost

```shell
npm run develop
```
hoặc
```shell
gatsby develop
```

## Build & Deploy dự án
```shell
gatsby build
```

Copy toàn bộ file trong thư mục `./public` lên server thư mục `/opt/blog`

Tạo file cấu hình Nginx:

`vim /etc/nginx/sites-enabled/blog`

Cấu hình Nginx Web Server trỏ tới thư mục chứa file build
```shell
server {
        listen 80;

        server_name blog.anhnbt.com;

        root /opt/blog;

        index index.html;

        location / {
                try_files $uri /index.html =404;
        }
}
```

## Cài đặt SSL
```shell
sudo apt install certbot python3-certbot-nginx
```

```shell
sudo certbot --nginx -d blog.anhnbt.com 
```

Đợi câu hỏi prompt hiện ra thì lần lượt làm theo các bước sau:
- Email: `anhnbt.it@gmail.com`
- Nhập `A`
- Nhập `N`
- Nhập `2`
