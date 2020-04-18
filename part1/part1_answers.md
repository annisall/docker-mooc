# Part 1

## 1.1 Getting started

*Docker ps -a* outputs:

```
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
89f61703f3be        nginx               "nginx -g 'daemon of…"   52 seconds ago      Exited (0) 18 seconds ago                       hopeful_jepsen
e57ad8d1f355        nginx               "nginx -g 'daemon of…"   54 seconds ago      Exited (0) 6 seconds ago                        angry_heyrovsky
302b3a81bf8d        nginx               "nginx -g 'daemon of…"   56 seconds ago      Up 54 seconds               80/tcp              unruffled_gates
8cf1c86578e6        nginx               "nginx -g 'daemon of…"   6 minutes ago       Exited (0) 5 minutes ago                        cool_gauss
```

Screenshot of the output: ![Screenshot of output, for rows which shows that there were three containers, two of which are stopped.](images/1_1.png)
## 1.2 Cleanup

*Docker ps -a* outputs: 

```
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

```


*Docker images* outputs:

```
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```

Sreenshots of both outputs: ![Screenshot of outputs, showing they're empty](images/1_2.png)

## 1.3 Hello Docker Hub

Command executed for completing the exercise (without output of downloading the image):
```
docker run -it devopsdockeruh/pull_exercise

Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```



Screenshot: 

![Screenshot with same contents as text above](images/1_3.png)

## 1.4 

Commands (without outputs) executed to complete the exercise:
```
docker run -d devopsdockeruh/exec_bash_exercise
docker container ls
docker exec -it beautiful_margulis bash
root@934a6179c912:/usr/app# tail -f ./logs.txt

```

The output of the last command:
```
Secret message is:
"Docker is easy"
Sat, 18 Apr 2020 14:26:20 GMT
Sat, 18 Apr 2020 14:26:23 GMT
Sat, 18 Apr 2020 14:26:26 GMT
Sat, 18 Apr 2020 14:26:29 GMT
read escape sequence
```

And cleaning up the container (because I didn't use --rm flag when running it):
```
docker container ls

CONTAINER ID        IMAGE                               COMMAND             CREATED             STATUS              PORTS               NAMES
934a6179c912        devopsdockeruh/exec_bash_exercise   "node index"        6 minutes ago       Up 6 minutes                            beautiful_margulis

docker stop beautiful_margulis

docker rm beautiful_margulis

docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

## 1.5 

Command run in terminal tab 1:
```
docker run -it --name curl-helsinki ubuntu:16.04 sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
Input website:
```

Command run in terminal tab 2:
```
docker attach --sig-proxy=false curl-helsinki
read escape sequence

docker exec -it curl-helsinki bash
root@8478dbdf4a10:/# apt install curl
```

Then again in terminal tab 1:
```
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
```

## 1.6 

Dockerfile produced [can be found here](dockerfiles/Dockerfile1_6)

And the commands that were used to build and run it:
``` 
docker build -t docker-clock .
docker run docker-clock
```
