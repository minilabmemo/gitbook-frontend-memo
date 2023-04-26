# docker

參考文章：[Docker 是怎麼實現的？前端怎麼用 Docker 做部署？](https://www.readfog.com/a/1678666807100149760)



### 撰寫dockerfile

* 第一種是http-server 雖然我在本地跑可以執行 docker build也成功，但執行時報錯 TBD
* 第二種是使用nginx 照說明先產生一個default.conf, 再改寫dockerfile

{% code title="default.conf" %}
```

server {
    listen       80;
    server_name  localhost;

    #charset koi8-r;
    access_log  /var/log/nginx/host.access.log  main;
    error_log  /var/log/nginx/error.log  error;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }
}

```
{% endcode %}

{% code title="dockerfile" %}
```

# build stage
FROM node:14.15.0 as build-stage

WORKDIR /app

COPY package.json ./

RUN npm install

COPY . .

RUN npm run build

# production stage
# FROM node:10

# WORKDIR /app

# COPY --from=build_image /app/dist ./dist

# RUN npm i -g http-server

# CMD http-server ./dist

FROM nginx  as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html

COPY --from=build-stage /app/default.conf /etc/nginx/conf.d/default.conf


EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

```
{% endcode %}

* 說明 [nginx -g "daemon off;" 你学废了吗](https://www.cnblogs.com/JulianHuang/p/15753732.html)



### docker build & run

接著執行

```
  docker build -t xxx . --no-cache
  docker run -p 80:80 xxx
  打開 http://localhost 看到網站了！
```
