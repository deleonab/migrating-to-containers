## Moving from a mysql web based application from a VM solution to a containerised one
---
### WE will first need to pull the MySQL base image from the Docker Hub Registry
### .

```
docker pull mysql/mysql-server:latest
```
![Install mysql](./images/install-mysql.JPG)

### The next step is to deploy the new MySQL container by running it
```
docker run --name mysql_container -e MYSQL_ROOT_PASSWORD="Olupero2023%mysql" -d mysql/mysql-server:latest
```
### some-mysql is the name you want to assign to your container, my-secret-pw is the password to be set for the MySQL root user and tag is the tag specifying the MySQL version you want.

### Let's check docker containers that are running using docker ps -a
```
docker ps -a
```
![mysql container](./images/mysql-container.JPG)

