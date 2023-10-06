## Link containers (deprecation warning due to Swarm)

> docker run -d --name=redis redis
> docker run -d --name=webapp-ui -p 3000:80 --link=redis:redis webapp-frontend

in python app:

```
...
def get_redis():
  if not hasattr(g, 'redis'):
    g.redis = Redis(host="redis", db=0, socket_connect_timeout=2, socket_timeout=2)
   return g.redis
...
```

for postgres:

> docker run -d --name=db -e POSTGRES_PASSWORD=postgres postgres
> docker run -d --name=webapp-api -p 3000:80 --link=postgres:postgres webapp-backend

in nodeJs app:
```
...
   pg.connect("postgres://postgres@db/postgres", "postgres", function (err, client, done) {
    if(err) {
        console.log("Waiting for db);
    }
    callback(err, client);
   });
...
```

also a worker c# app:
> docker run -d --name=worker --link=redis:redis --link=db:db worker

in C# app:
```
...
try {
    Jedis redis = connectToRedis("redis");
    Connection dbConn = connectToDb("db");

    System.err.println("Connected to redis and postgresql");
}

...
```

for the `docker-compose.yml` file:

```
redis:
    image: redis

webapp-ui:
    image: webapp-frontend
    ports:
        - "3000:80"
    links:
        - redis

db:
    image: postgres
    environment:
        - POSTGRES_PASSWORD=postgres

webapp-api:
    image: webapp-backend
    ports:
        - "3000:80"
    links:
        - db

worker:
    image: worker
    links:
        - redis
        - db
```

it's also possible to instruct docker-compose to build the images of the application files

```
redis:
    image: redis

webapp-ui:
    build: ./webapp-frontend
    ports:
        - "3000:80"
    links:
        - redis

db:
    image: postgres
    environment:
        - POSTGRES_PASSWORD=postgres

webapp-api:
    build: ./webapp-backend
    ports:
        - "3000:80"
    links:
        - db

worker:
    build: ./webapp-worker
    links:
        - redis
        - db
```