FROM golang:1.15.15-buster

ENV GO111MODULE=on

WORKDIR /tmp/tools
COPY go.mod .

RUN go install golang.org/x/tools/gopls

WORKDIR /go