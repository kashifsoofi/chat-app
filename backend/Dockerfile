FROM golang:1.18-bullseye AS build

WORKDIR app

COPY go.mod ./
COPY go.sum ./

RUN go build -o /chat-server

FROM debian:bullseye-slim

WORKDIR /app

COPY --from=build /chat-server /chat-server

EXPOSE 8080

USER app:app

ENTRYPOINT [ "chat-server" ]
