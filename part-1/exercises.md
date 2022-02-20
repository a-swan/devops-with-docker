# DevOps with Docker Exercises Part 1

## Exercise 1.1: Getting started

```bash
 $ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS                     PORTS     NAMES
7fb7f5d09804   nginx     "/docker-entrypoint.…"   25 seconds ago       Exited (0) 1 second ago              loving_wu
8c0cee791f12   nginx     "/docker-entrypoint.…"   33 seconds ago       Up 32 seconds              80/tcp    practical_einstein
4d74ff3364d6   nginx     "/docker-entrypoint.…"   About a minute ago   Exited (0) 6 seconds ago             elegant_raman
```

## Exercise 1.2: Cleanup

```bash
 $ docker ps -a
CONTAINER ID    IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

 $ docker images
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
```

## Exercise 1.3: Secret message

**Secret Message:** "You can find the source code here: https://github.com/docker-hy "

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

```bash
 $ docker run -it --name website ubuntu sh -c 'apt update; apt install curl; echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
```

If only there was a way to install curl right to the ubuntu image :thinking: :thinking: :thinking: :thinking:

## Exercise 1.5: Size of images

```bash
 $ docker run -d -it --name alpine-secret devopsdockeruh/simple-web-service:alpine
9b462df2a33f1d27972fe264aacfb8efa0ce28cc2e7fca29886b27be7af673da
 $ docker exec -it alpine-secret sh
/usr/src/app # tail -f text.log
2022-02-20 19:23:27 +0000 UTC
2022-02-20 19:23:29 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
2022-02-20 19:23:31 +0000 UTC
2022-02-20 19:23:33 +0000 UTC
2022-02-20 19:23:35 +0000 UTC
2022-02-20 19:23:37 +0000 UTC
2022-02-20 19:23:39 +0000 UTC
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
2022-02-20 19:23:41 +0000 UTC
2022-02-20 19:23:43 +0000 UTC
2022-02-20 19:23:45 +0000 UTC
^C
/usr/src/app #
```

## Exercise 1.6: Hello Docker Hub

**Secret Message:** "This is the secret message"

```bash
 $ docker run -it devopsdockeruh/pull_exercise
Unable to find image 'devopsdockeruh/pull_exercise:latest' locally
latest: Pulling from devopsdockeruh/pull_exercise
8e402f1a9c57: Pull complete
5e2195587d10: Pull complete
6f595b2fc66d: Pull complete
165f32bf4e94: Pull complete
67c4f504c224: Pull complete
Digest: sha256:7c0635934049afb9ca0481fb6a58b16100f990a0d62c8665b9cfb5c9ada8a99f
Status: Downloaded newer image for devopsdockeruh/pull_exercise:latest
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```

## Exercise 1.7: Two line Dockerfile

```bash
 $ docker build . -t web-server
[+] Building 0.1s (5/5) FINISHED
 => [internal] load build definition from Dockerfile       0.0s
 => => transferring dockerfile: 100B                       0.0s
 => [internal] load .dockerignore                          0.0s
 => => transferring context: 2B                            0.0s
 => [internal] load metadata for docker.io/devopsdockeruh  0.0s
 => [1/1] FROM docker.io/devopsdockeruh/simple-web-servic  0.0s
 => exporting to image                                     0.0s
 => => exporting layers                                    0.0s
 => => writing image sha256:978fbf315695ef5a3ec2e77ee411c  0.0s
 => => naming to docker.io/library/web-server              0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
 $ docker run web-server
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:	export GIN_MODE=release
 - using code:	gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /*path                    --> server.Start.func1 (3 handlers)
[GIN-debug] Listening and serving HTTP on :8080
```

[Dockerfile]()

## Exercise 1.8: Image for Script

[Dockerfile]()

## Exercise 1.9: Volumes

```bash
 $ docker run -v "$(pwd)/text.log:/usr/src/app/text.log" devopsdockeruh/simple-web-service
```

## Exercise 1.10: Ports open

```bash
 $ docker run -p 3000:8080 web-server
```
