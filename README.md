# Boilerplate Symfony5.4 (PHP 8.1) + Mariadb + Nginx

**Disclaimer**: This repo is suitable for testing/dev only. For use in production change the congigs in `docker-compose.yaml` and `.env`
and delete them from the VCS.

## Services
* PHP:8.1
  * [Dockerhub](https://hub.docker.com/layers/php/library/php/8.1.1-fpm/images/sha256-43eccbf9fbcca390a2837c5e079ae61b743f206f20b92ccd60f215812c15cc7d?context=explore)
  * with custom Dockerfile
  * FastCGI server (php-fpm) listening on port 9100
* Nginx as web-server, listening on port 80 and exposing port 8081
  * with a custom Dockerfile and a 
  * custom `default.conf`
* Mariadb 10.7.1

The Symfony skeleton is the standard (empty) Symfony 5.4 skeleton
