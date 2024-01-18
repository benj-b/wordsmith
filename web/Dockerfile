FROM golang:latest AS build
WORKDIR /src
COPY dispatcher.go dispatcher.go
RUN go build -o dispatcher dispatcher.go
EXPOSE 80

# ---------------------------------------

FROM ubuntu:latest
WORKDIR /app
COPY --from=build /src/dispatcher /app/dispatcher
COPY static ./static
CMD ["./dispatcher"]

# ---------------------------------------

## Correction

# FROM golang:alpine AS builder
# COPY dispatcher.go .
# RUN go build dispatcher.go

# FROM alpine
# COPY --from=bulider /go/dispatcher .
# COPY static static
# CMD [ "./dispatcher" ]