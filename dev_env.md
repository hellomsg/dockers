## create network
docker network create my_net
## mysql
docker run --name mysql5.7 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root --network my_net --network-alias mysqlserver -d mysql:5.7
## mysql client
docker run -it --rm --network my_net mysql:5.7 mysql -hmysql5.7 -uroot -p
## memcached
docker run --name memcached -p 11211:11211 --network my_net --network-alias memcached  -d memcached:latest  -m 64
## mongodb
docker run --name mongo -p 27017:27017 --network my_net --network-alias mongo -d mongo:latest
## zookeeper & kafka
docker run -d -e ALLOW_ANONYMOUS_LOGIN=yes --name zookeeper-server -p 2181:2181 --network my_net bitnami/zookeeper:latest
docker run -d --name kafka-server01000 -p 9092:9092 --network my_net -e KAFKA_ZOOKEEPER_CONNECT=zookeeper-server:2181 -e KAFKA_ADVERTISED_HOST_NAME=kafka-server01000 -e KAFKA_ADVERTISED_PORT=9092 wurstmeister/kafka:0.10.0.0
host: 127.0.0.1 kafka-server01000
