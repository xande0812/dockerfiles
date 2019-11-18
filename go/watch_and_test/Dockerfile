FROM golang:1.13.4-alpine3.10 as builder

RUN apk --no-cache add ca-certificates gcc libc-dev git

RUN go get github.com/eaburns/Watch

ENV GO111MODULE=on

WORKDIR /go/src/app
COPY go.mod .
COPY go.sum .

RUN go mod download

FROM builder AS tester

WORKDIR /go/src/app

ENTRYPOINT ["Watch", "-t", "go", "test", "-v"]
