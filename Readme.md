# contao

## http://localhost/contao-manager.php

#### start docker container as a new project:
```
cd ~/path/to/project
docker run --name contao -d -p 80:80 -v contao-mysql-${PWD##*/}:/var/lib/mysql pagestyles/contao
```
#### copy newly created contao web-root from container to host:
```
cd ~/path/to/project
docker cp contao:/var/www/html _page
```

#### mysqldump contao database
```
cd ~/path/to/project
docker exec -t contao mysqldump --databases contao > mysqldump
```

---
#### start existing project
```
cd ~/path/to/project
docker run --name contao -d -p 80:80 -v $PWD/_page:/var/www/html -v contao-mysql-${PWD##*/}:/var/lib/mysql pagestyles/contao
```

#### import existing mysqldump
```
cd ~/path/to/project
docker exec -t contao mysql < mysqldump
```
