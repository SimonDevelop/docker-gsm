# docker-gsm

Just need clone the project and launch the clone command in docker-gsm :
```
git clone https://github.com/SimonDevelop/game-server-manager.git symfony
```

And juste launch dockers with `docker-compose up -d`

You have a cron job to add for the verification of the game servers :
```
*/5 * * * * docker exec <container_php> php bin/console cron:server:check >/dev/null 2>&1
example :
*/5 * * * * docker exec game-server-manager-php-1 php bin/console cron:server:check >/dev/null 2>&1
```

### NOTE
This is the directory for the docker development environment of the [game-server-manager](https://github.com/SimonDevelop/game-server-manager) project. You can use it as inspiration to build your production environment.
