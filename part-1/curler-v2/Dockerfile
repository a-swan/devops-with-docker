FROM ubuntu:20.04

WORKDIR /usr/src/app

COPY website.sh .

RUN chmod +x website.sh

RUN apt -y update && apt -y install curl

ENTRYPOINT [ "./website.sh" ]
