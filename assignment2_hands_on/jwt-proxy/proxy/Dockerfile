FROM golang:1.23 AS build
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 go build -o /proxy .

FROM gcr.io/distroless/static
COPY --from=build /proxy /proxy
EXPOSE 85
ENTRYPOINT ["/proxy"]