# gacha-docker

Apache+mod_php / MySQL

## Environment
### 1.docker install
https://hub.docker.com/search/?offering=community&type=edition
install from above

### 2.git clone
git clone in certain directory of your local PC

### 3.clone source code
clone the source code from the repository on `dev-docker/www/` directory

### 4.Configure VirtualHost
`dev-docker/web/apache-conf/` 
There is the template （gacha.conf） of VirtualHos in `dev-docker/web/apache-conf/` and make the config of VirtualHost based it.

### 5.Configure hosts of local
Add `127.0.0.1 [Domain configured in VirtualHost]` on `/etc/hosts` (if you use MacOS).

### 6.docker build
Run `docker-compose build` to build.

### 7.Start the container
Run `docker-compose up -d` to start the container.

### 8.Access
If you can access to the domain that you configured, you're ready!

## Others
### Container info
dev-docker_db_1 →　DB container  
dev-docker_redis_1 →　Redis container  
dev-docker_web_1　→　Web container 

### ssh to each container
ssh to web container by `docker-compose exec web bash`  
*If you change the part of `web` into `db` or `redis`, you can login via ssh to them.

### DB access
After you login with ssh to db container by `docker-compose exec db bash`, you can login to mysql by `mysql -uroot -proot`
