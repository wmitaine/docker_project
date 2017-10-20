# docker_project


### Stack


* haProxy
* ~~MariaDB~~
* sqlite
* ~~Nginx~~
* Cloud
  - OwnCloud:fpm
  - NextCloud nextcloud:fpm
  - CozyCloud
* Wallabag
  - wallabag
  -
* Wekan
* ~~Wordpress~~
* Meteor




### MariaDB
```
docker run --name mariadb 
		-v /home/willi/Workspace/Docker/Data/MariaDB:/var/lib/mysql 
		-e MYSQL_ROOT_PASSWORD=my-secret-pw 
		-d mariadb:latest
```

```bash
docker run --name mariadb -e MYSQL_ROOT_PASSWORD=azerty -v /home/willi/Workspace/Docker/Data/MariaDB:/var/lib/mysql -d mariadb:latest</code>
```

### PhpMyAdmin
```bash
docker run --name myadmin -e PMA_HOST=mariadb --link mariadb -e MYSQL_ROOT_PASSWORD=azerty -p 8080:80 -d phpmyadmin/phpmyadmin</code>
```

### Wordpress
```bash
docker run --name wordpress --link mariadb -v /home/willi/Workspace/Docker/Data/Wordpress:/var/www/html -e WORDPRESS_DB_HOST=mariadb -e WORDPRESS_DB_USER=wordpress -e WORDPRESS_DB_PASSWORD=azerty -e WORDPRESS_DB_PASSWORD=wordpress -p 80:80 -d wordpress</code>
```


### Notes

HaProxy qui écoute sur les port nécessaire (80, 443, 21, etc) qui redirige vers les services adéquates

Reverse Proxy ou Proxy qui n'écoute que sur le 80 et qui redistribue vers les services qui vont bien : 
</br>blog.truc.fr => vers docker nginx en 80
</br>meteor.truc.fr => vers docker metor en 5000
</br>Etc 

Il faudra peut etre lié les docker sur un réseau de type bridge ou autre