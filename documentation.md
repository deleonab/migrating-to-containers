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

### Next we shall create a mysql client container and a mysql server container.
# First let us create the network they will be attached to.

### I stopped and removed the previously created container and verified the removal
```
docker ps -a
docker stop mysql_container
docker rm mysql_container
```

### I will create a network which is of  DRVER type Bridge  by default

```
docker network create --subnet=172.18.0.0/24 web_app_network
```

### Network created successfullly

![network created](./images/network-created.JPG)

### For security, I will create an environment variable to store the root password
