# rclgo example

cf. https://github.com/tiiuae/rclgo

## Getting started

```
$ UID=$(id -u) GID=$(id -g) docker compose build
$ docker compose up -d
$ docker compose exec --index=1 ros2 bash
```

In the container

```
$ cd mytest
$ pushd greeting_msgs
$ source /opt/ros/humble/local_setup.sh
$ colcon build
$ source ./install/local_setup.sh
$ popd
$ go mod tidy
$ go install github.com/tiiuae/rclgo/cmd/rclgo-gen@latest
$ export PATH=$HOME/go/bin:$PATH
$ rclgo-gen generate -d msgs
$ go build -o pub ./publisher
$ go build -o sub ./subscriber
```

```
$ ./sub &
$ ./pub
```

```
$ docker-compose down
```
