# show running containers
docker ps

# show all containers
docker ps -a

# run one time command in the container
docker run busybox ls

# docker run = docker create + docker start

# remove unused containers and images
docker system prune

# executing commands in running container
terminal 1:
  docker run redis
terminal 2:
  docker exec -it <containerId> redis-cli

# start shell within a running container
docker exec -it <containerId> sh

# start shell within a new container
docker run -it busybox sh


# build container and push it to dockerhub
sudo docker build -t paladinze/react_playground -f Dockerfile .
sudo docker push paladinze/react_playground:latest


# run containers using docker-compose
docker-compose up -d

# run containers & rebuild the images
docker-compose up -d --build


# run mysql container
docker run --name mysql -e MYSQL_ROOT_PASSWORD=921021 -d -p 3306:3306 -v mysql_data:/var/lib/mysql/data mysql

# run postgres container
docker run --name postgres -e POSTGRES_PASSWORD=921021 -d -p 5432:5432 -v postgres_data:/var/lib/postgresql/data postgres

# generate encrypted docker hub password in travis
travis encrypt REGISTRY_PASS=Zfmttm01 --add env.global
