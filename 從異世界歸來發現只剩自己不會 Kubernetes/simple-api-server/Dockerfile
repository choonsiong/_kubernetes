FROM golang:1.24.5 AS builder

WORKDIR /app

COPY . .

ENV CGO_ENABLED=0
ENV GOOS=linux
ENV GOARCH=amd64

RUN go mod tidy
RUN go build -o main

FROM alpine:3.22

WORKDIR /

COPY --from=builder /app/main .

EXPOSE 8080

ENTRYPOINT ["./main"]
