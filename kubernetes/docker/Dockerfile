############################
# STEP 1 build executable binary
############################
FROM golang:latest AS builder
RUN mkdir /app
ADD . /app
WORKDIR /app/go-app
# Using go get.
RUN go get -d -v
# Build the binary.
RUN CGO_ENABLED=0 GOOS=linux go build -o main .

############################
# STEP 2 build a small image
############################
FROM alpine:latest
# Copy our static executable.
COPY --from=builder /app .
# Run the main binary.
CMD ["./go-app/main"]