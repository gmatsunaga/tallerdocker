
docker login -u gustavomatsunaga  docker.io

docker pull nicopaez/pingapp:3.0.0

docker image tag nicopaez/pingapp:3.0.0 gustavomatsunaga/pingapp:3.0.0

docker image push gustavomatsunaga/pingapp:3.0.0

docker pull gustavomatsunaga/pingapp:3.0.0

