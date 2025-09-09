# acp-
由于我要报考acp云计算方向的证书，就自己做了一个答题网站，本人没有开发经验，只有一年的运维经验，代码完全由AI开发，所以存在瑕疵。
网页体验网址：www.waidati.top

并且我已经将前端页面和后端处理程序均打包成了docker镜像，拉取即可使用。

后端程序：
  首先拉取镜像：
    docker pull crpi-311afc0hn3w14sku.cn-beijing.personal.cr.aliyuncs.com/image-cangku/apc-dati:v1
    镜像启动参数：
        数据库题库地址:DB_HOST=1.1.1.1
        数据库用户名：DB_USER=root
        数据库用户密码：USER_PW=123456
        数据库库名：DB_NAME=questions_db
        端口：3000
      例如：
       docker run -d --network app-net \
       -e DB_HOST=1.1.1.1 \
       -e DB_USER=root \
       -e USER_PW=123456 \
       -e DB_NAME=questions_db \
       --name app crpi-311afc0hn3w14sku.cn-beijing.personal.cr.aliyuncs.com/image-cangku/apc-dati:v1


前端页面：
  首先拉取镜像：
    docker pull crpi-311afc0hn3w14sku.cn-beijing.personal.cr.aliyuncs.com/image-cangku/apc-nginx:v2
    镜像启动参数：
        域名：HOST_NAME=www.template.com
        后端答题地址：APP_HOST=1.1.1.1
        容器内证书目录（pem/key）：/usr/local/openresty/nginx/certs/
        端口：80 443
    例如：
      docker run -d --network app-net \
      -e HOST_NAME=www.template.com \
      -e APP_HOST=app \
      -v /nginx/certs/:/usr/local/openresty/nginx/certs/
      -p 80:80 -p 443:443 \
      --name nginx crpi-311afc0hn3w14sku.cn-beijing.personal.cr.aliyuncs.com/image-cangku/apc-nginx:v2

 数据库：
   导入数据文件即可，我使用的是MySQL数据库。

