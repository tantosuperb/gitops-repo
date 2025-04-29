FROM golang:1.20 AS builder
WORKDIR /app
COPY . .
RUN go build -o shopping-web

FROM alpine:latest
COPY --from=builder /app/shopping-web /shopping-web
ENTRYPOINT ["/shopping-web"]
