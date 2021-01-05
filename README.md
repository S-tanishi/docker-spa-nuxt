# docker-spa-nuxt
```
$ docker-compose exec ui yarn create nuxt-app frontend

# 認証・APIとの通信に必要なライブラリの追加
docker-compose exec ui yarn add @nuxtjs/auth @nuxtjs/axios @nuxtjs/proxy

SASSで開発できるようにライブラリを追加
docker-compose exec ui yarn add --dev sass sass-loader fibers

$ docker-compose exec ui yarn dev 
```