# docker_project

Stack
	haProxy
	MariaDB
	sqlite
	Nginx
	Cloud
		-OwnCloud:fpm
		-NextCloud nextcloud:fpm
		-CozyCloud
	Wallabag
		-wallabag
		-
	Wekan
	Wordpress




MariaDB
	docker run --name mariadb 
		-v /home/willi/Workspace/Docker/Data/MariaDB:/var/lib/mysql 
		-e MYSQL_ROOT_PASSWORD=my-secret-pw 
		-d mariadb:latest

	 docker run --name mariadb -e MYSQL_ROOT_PASSWORD=azerty -v /home/willi/Workspace/Docker/Data/MariaDB:/var/lib/mysql -d mariadb:latest

PhpMyAdmin
	docker run --name myadmin -e PMA_HOST=mariadb --link mariadb -e MYSQL_ROOT_PASSWORD=azerty -p 8080:80 -d phpmyadmin/phpmyadmin

Wordpress
	docker run --name wordpress --link mariadb -v /home/willi/Workspace/Docker/Data/Wordpress:/var/www/html -e WORDPRESS_DB_HOST=mariadb -e WORDPRESS_DB_USER=wordpress -e WORDPRESS_DB_PASSWORD=azerty -e WORDPRESS_DB_PASSWORD=wordpress -p 80:80 -d wordpress




HaProxy qui écoute sur les port nécessaire (80, 443, 21, etc) qui redirige vers les services adéquates

Reverse Proxy ou Proxy