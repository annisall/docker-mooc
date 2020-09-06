Here are my answers to part 2 of docker mooc.

## 2.1
Docker compose file that mounts the file can be found [here](projects/2_1/docker-compose.yml). When logs.txt file exists, it can be run with ```docker-compose up``` command.

## 2.2
Docker compose file that is used to run the service in port 80 can be found [here](projects/2_2/docker-compose.yml). 

## 2.3
Docker compose file for running both bakcend and frontend can be found [here](projects/2_3/docker-compose.yml). Since I put the environment variables to docker-compose.yml, I was able to remove them from the Dockerfiles.

## 2.4
To scale the compute servers I run following command:
```docker-compose up --scale compute=3```

## 2.5
The docker-compose.yml that has redis in addition to frontend and backend can be found [here](projects/2_5/docker-compose.yml).

## 2.6
The docker-compose.yml with database included can be found [here](projects/2_6/docker-compose.yml)

## 2.7
After building images for [frontend](https://github.com/docker-hy/ml-kurkkumopo-frontend), [backend](https://github.com/docker-hy/ml-kurkkumopo-backend) and [training](https://github.com/docker-hy/ml-kurkkumopo-training) I created a docker-compose.yml which can be found [here](projects/2_7/docker-compose.yml).

## 2.8
Docker-compose.yml file that has services for frontend, backend,redis, postgresql and nginx can be found [here](projects/2_8/docker-compose.yml). Alogn with the docker-compose file one would need nginx.conf file in the same directory with following content:
```
events { worker_connections 1024; }

  http {
    server {
      listen 80;

      location / {
        proxy_pass http://frontti:5000/;
      }

      location /api/ {
        proxy_pass http://bakki:8000/;
      }
    }
  }
```