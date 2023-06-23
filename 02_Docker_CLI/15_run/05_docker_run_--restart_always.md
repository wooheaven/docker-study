```
docker run -itd \
-e "TZ=Asiz/Seoul" \
-e POSTGRES_PASSWORD=123qwe \
-v `pwd`/var2/lib/postgresql/data:/var/lib/postgresql/data \
-p 55432:5432 \
--name pg15.3 \
--network postgres-network \
--restart always \
postgres:15.3
```
