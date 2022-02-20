# DevOps with Docker Exercises Part 1

## Exercise 1.1: Getting started

```
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS                     PORTS     NAMES
7fb7f5d09804   nginx     "/docker-entrypoint.…"   25 seconds ago       Exited (0) 1 second ago              loving_wu
8c0cee791f12   nginx     "/docker-entrypoint.…"   33 seconds ago       Up 32 seconds              80/tcp    practical_einstein
4d74ff3364d6   nginx     "/docker-entrypoint.…"   About a minute ago   Exited (0) 6 seconds ago             elegant_raman
```

## Exercise 1.2: Cleanup

```
$ docker ps -a
CONTAINER ID    IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
```

## Exercise 1.3: Secret message

**Secret Message:** You can find the source code here: https://github.com/docker-hy

```bash
 $ docker run -d -it --name secret devopsdockeruh/simple-web-service:ubuntu
95b15a97fa814d243269ae60de5147ab2a0abffc3b6b30be16a7beaf330040c6
 $ docker exec -it secret bash
root@95b15a97fa81:/usr/src/app# tail -f text.log
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
2022-02-19 19:12:31 +0000 UTC
2022-02-19 19:12:33 +0000 UTC
2022-02-19 19:12:35 +0000 UTC
2022-02-19 19:12:37 +0000 UTC
2022-02-19 19:12:39 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
2022-02-19 19:12:41 +0000 UTC
2022-02-19 19:12:43 +0000 UTC
2022-02-19 19:12:45 +0000 UTC
2022-02-19 19:12:47 +0000 UTC
2022-02-19 19:12:49 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
2022-02-19 19:12:51 +0000 UTC
2022-02-19 19:12:53 +0000 UTC
2022-02-19 19:12:55 +0000 UTC
^C
root@95b15a97fa81:/usr/src/app#
```

## Exercise 1.4: Missing Dependencies
