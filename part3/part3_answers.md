Here are my answers to docker mooc part 3.

## 3.1
I use backend Dockerfile and frontend Dockerfile from exercise 1.11 as a base versions before optimizing.
The size of the images after build are 325MB (backend) and 519MB (frontend).

After combining RUN commands into one, backend image size is at 323MB. Frontend image is at 517MB. 

After removing curl and /var/lib/apt/lists/* the image size is 292MB for backend and 487MB for frontend. I also added cleaning npm cache, which lead to images go down to 292MB (backend) and 486MB (frontend). I tested, and everything seemed to work after the changes, so those are the final image sizes for now. I don't think there's anything else that is extra.

The final version of Dockerfile for backend is [here](projects/3_1/Dockerfile_backend) and for frontend [here](projects/3_1/Dockerfile_frontend).

## 3.2

