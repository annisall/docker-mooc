Here are my answers to docker mooc part 3.

## 3.1
I use backend Dockerfile and frontend Dockerfile from exercise 1.11 as a base versions before optimizing.
The size of the images after build are 325MB (backend) and 519MB (frontend).

After combining RUN commands into one, backend image size is at 323MB. Frontend image is at 517MB. 

After removing curl and /var/lib/apt/lists/* the image size is 292MB for backend and 487MB for frontend. I also added cleaning npm cache, which lead to images go down to 292MB (backend) and 486MB (frontend). I tested, and everything seemed to work after the changes, so those are the final image sizes for now. I don't think there's anything else that is extra.

The final version of Dockerfile for backend is [here](projects/3_1/Dockerfile_backend) and for frontend [here](projects/3_1/Dockerfile_frontend).

## 3.2
I decided I wanted to create a github actions ci/cd pipeline to deploy the [course materials](https://devopswithdocker.com/) to heroku. I forked the course github repository](https://github.com/docker-hy/docker-hy.github.io) under my account  here](https://github.com/annisall/docker-hy.github.io). To get the course material to heroku I needed to create a conf for github actions pipeline, and also a configuration for nginx so that it works with Heroku. Heroku assigns a random port for the app, so it doesn't work with default nginx configuration. 

The github actions configuration file can be found [here](https://github.com/annisall/docker-hy.github.io/blob/master/.github/workflows/jekyll.yml) and the configuration file for nginx [here](https://github.com/annisall/docker-hy.github.io/blob/master/nginx.conf). To make it all work together, I altered the Dockerfile that already existed and the altered version can be found [here](https://github.com/annisall/docker-hy.github.io/blob/master/Dockerfile).



