FROM golang AS build

WORKDIR /backend
COPY go.mod go.sum ./
RUN ["go", "build", "github.com/mattn/go-sqlite3", "gopkg.in/yaml.v3"]
COPY . .
COPY faucetd.yaml /out/
RUN ["go", "build", "-o", "/out/faucetd", "faucet/cmd/faucetd"]

FROM debian
COPY --from=build /out /
WORKDIR /data
RUN ["/faucetd", "db", "create", "/faucetd.yaml"]
EXPOSE 5000
ENTRYPOINT ["/faucetd", "serve", "/faucetd.yaml"]
