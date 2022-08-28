FROM golang:1.15.6-alpine3.12

WORKDIR /go/src/github.com/nickolastone/ws

COPY go.mod .
COPY go.sum .
RUN go mod download

COPY . .
ENV CGO_ENABLED=0
RUN go test -c -tags autobahn -coverpkg "github.com/nickolastone/ws/..." github.com/nickolastone/ws/example/autobahn

CMD ["./autobahn.test", "-test.coverprofile", "/report/server.coverage"]
