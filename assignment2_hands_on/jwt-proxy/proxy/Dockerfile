FROM golang:1.27 AS build
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 go build -o /proxy .

FROM scratch
COPY --from=build /proxy /proxy
EXPOSE 85
ENTRYPOINT ["/proxy"]