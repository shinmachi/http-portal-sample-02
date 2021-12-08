# https-portal をローカルで試す
- 動作環境: Mac OS
- 参考元
  - https://blog.kai-lab.com/local_ssl_with_https_portal/
  - https://github.com/nobiki/https-portal-sample

# 実行
```
$ docker-compose build && docker-compose up -d
```

# default.conf
- 必要最小限の設定です。 
- listenのポートやserver_nameがdocker-compose.ymlで指定しているものになっているかを必ず確認してください。

# /etc/hosts を書き換える
```
$ sudo vi /etc/hosts
127.0.0.1       test.local # これを追記
```

```
browser: localhost -> container: http://web:8008

# docker-compose.yml 
https-port
    DOMAINS: 'test.local -> http://web:8008'

# default.conf
nginx 
    listen: 8008
    server_name: localhost 
```