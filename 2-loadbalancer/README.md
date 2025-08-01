# 로드밸런서용
무중단 배포를 위해 nginx 를 사용할 수 있다.


# 실행 방법:
## 1. nginx 에서 사용할 conf 지정 (nginx-route-to-localhost.conf 를 사용)
```
$ ln -sf nginx-route-to-localhost.conf active.conf
```
## 2. nginx 실행
```
# 기본적으로 active.conf 를 참고하도록 되어있어서 active.conf 를 읽음
$ docker-compose up
```

##  만약 다른 conf 를 사용하고자 할 경우 (ex: nginx-route-to-1.conf)
```
# nginx 에서 사용할 conf 지정 (nginx-route-to-1.conf 를 사용)
$ docker exec -w /etc/nginx/includes nginx-lb ln -sf nginx-route-to-1.conf active.conf
# 재기동
$ docker exec nginx-lb nginx -s reload
```
