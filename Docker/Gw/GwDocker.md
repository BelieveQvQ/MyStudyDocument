## 运行

```shell
docker run -d -p 8199:8199 --name mygw -v \ /home/t1gerhead/mygw/config:/var/www/Gw_v4/config \
--network my-net \
believeqvq/gw:test

docker run -d -p 8199:8199 --name mygw --network my-net -v /home/t1gerhead/gw/config:/var/www/Gw_v4/config believeqvq/gw:test

docker run -d -p 8299:8299 --name mygwrsa --network my-net -v /home/t1gerhead/gwrsa/config:/var/www/Gw_v4/config believeqvq/gw:rsa

docker pull believeqvq/gw:rsa
```

