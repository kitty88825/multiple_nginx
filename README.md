# 題目
* Two NGINX service
* project_one
    * show one on index page
    * domain: one.prj.com
* project_two
    * show two on index page
    * domain: two.prj.com
* target dynamic add new project_three with same CI/CD script
* project_three
    * show three on index page
    * domain: three.prj.com
* HINT docker-compose -f

# 想考
- 多個 docker-compose
- 反向代理
- nginx (N+1 proxy)

# dockerfile
```
FROM nginx:alpine
COPY index.html /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
```

# nginx.conf
```
server {
    listen 80;
    listen [::]:80;
    server_name one.prj.com;
    root /usr/share/nginx/html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```


# 思考分界線
# multiple_nginx
