# rclgo example

cf. https://github.com/tiiuae/rclgo

## Getting started

### Build

```
$ UID=$(id -u) GID=$(id -g) docker compose build
```

### Start

```
$ docker compose up -d --scale ros2=2
```

### Subscriber

```
$ docker compose exec --index=1 ros2 bash
$ cd mytest
$ pushd greeting_msgs
$ source /opt/ros/humble/setup.sh
$ colcon build
$ source ./install/local_setup.sh
$ popd
$ go mod tidy
$ go generate
$ go build -o sub ./subscriber
$ ./sub
```

### Publisher

```
$ docker compose exec --index=2 ros2 bash
$ cd mytest
$ source /opt/ros/humble/setup.sh
$ source ./greeting_msgs/install/local_setup.sh
$ go build -o pub ./publisher
$ ./pub
```

### Stop

```
$ docker compose down
```
