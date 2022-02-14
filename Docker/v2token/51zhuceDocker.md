## 运行

```shell
docker run -d -p 8000:8000 --name myv2token -v \ /home/t1gerhead/v2token/config:/app/config \
--network my-net \
believeqvq/v2token:test

docker run -d -p 8000:8000 --name myv2token -v /home/t1gerhead/v2token/config:/app/config --network my-net believeqvq/v2token:test

docker pull believeqvq/v2token:test
```

