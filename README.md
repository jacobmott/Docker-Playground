## Docker notes

### Connecting to mongo via bash/shell on running docker container

<details>

Running a bash/shell terminal for a running container from the command line
```
[5.2][503][jacob@jakesbeastmech][/d/OtherProjects/Docker-Playground]
$docker exec -it 137fe3371997 sh
# ls
bin  boot  data  dev  docker-entrypoint-initdb.d  etc  home  js-yaml.js  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
#
```
One your inside a shell in your continer for mongo.. you can do a mongosh to connect to mongodb
```
# mongosh
Current Mongosh Log ID: 66ae95ec385357b559149f47
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.2.10
Using MongoDB:          7.0.12
Using Mongosh:          2.2.10

For mongosh info see: https://docs.mongodb.com/mongodb-shell/


To help improve our products, anonymous usage data is collected and sent to MongoDB periodically (https://www.mongodb.com/legal/privacy-policy).
You can opt-out by running the disableTelemetry() command.

------
   The server generated these startup warnings when booting
   2024-08-03T20:36:00.216+00:00: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
   2024-08-03T20:36:00.694+00:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
   2024-08-03T20:36:00.694+00:00: /sys/kernel/mm/transparent_hugepage/enabled is 'always'. We suggest setting it to 'never' in this binary version
   2024-08-03T20:36:00.694+00:00: vm.max_map_count is too low
------

test>
```

</details>

### Sample mongodb connection strings

<details>

```
mongodb://<username>:<password>@<host>:<port>/<database>?directConnection=true
mongodb://user:pass@localhost:27017/myDatabase?directConnection=true

```
</details>

### Inspect the volumnes that docker compose creates

<details>

If you create a volume like this in docker compose file
```
volumes:
  MONGO_DATA:
    name: MONGO_DATA
  MONGO_CONFIG:
    name: MONGO_CONFIG
```

</details>


You can inspect it to see where its mounted on windows like this

<details>

```
[5.2][504][jacob@jakesbeastmech][/d/OtherProjects/Docker-Playground]
$docker volume ls
DRIVER    VOLUME NAME
local     MONGO_CONFIG
local     MONGO_DATA
[5.2][505][jacob@jakesbeastmech][/d/OtherProjects/Docker-Playground]
$docker volume MONGO_DATA

Usage:  docker volume COMMAND

Manage volumes

Commands:
  create      Create a volume
  inspect     Display detailed information on one or more volumes
  ls          List volumes
  prune       Remove unused local volumes
  rm          Remove one or more volumes
  update      Update a volume (cluster volumes only)

Run 'docker volume COMMAND --help' for more information on a command.
[5.2][506][jacob@jakesbeastmech][/d/OtherProjects/Docker-Playground]
$docker volume inspect MONGO_DATA
[
    {
        "CreatedAt": "2024-08-03T23:34:48Z",
        "Driver": "local",
        "Labels": {
            "com.docker.compose.project": "docker-playground",
            "com.docker.compose.version": "2.28.1",
            "com.docker.compose.volume": "MONGO_DATA"
        },
        "Mountpoint": "/var/lib/docker/volumes/MONGO_DATA/_data",
        "Name": "MONGO_DATA",
        "Options": null,
        "Scope": "local"
    }
]
```
</details>

### Links to good mongo stuff

<details>

https://www.youtube.com/watch?v=xBbSR7xU2Yw

</details>


