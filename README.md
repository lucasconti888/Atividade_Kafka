# Atividade_Kafka

## Primeiro, após a adição do arquivo yml com seu respectivo código, é preciso rodar o docker-compose com o seguinte comando:

docker-compose up -d

## Após isso, o seguinte comando permite que o usuário visualize o nome do container kafka criado:

docker ps

## Deve ser criado, então, o tópico para consumo e produção das mensagens:

docker exec -it <nome_do_container_kafka> /opt/kafka/bin/kafka-topics.sh --create --topic test-topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

## Por fim, em um terminal pode ser feita a produção de mensagens:

docker exec -it <seu_nome_do_container_kafka> /opt/kafka/bin/kafka-console-producer.sh --topic test-topic --bootstrap-server localhost:9092

## e, em outro, pode ser feita a visualização ou o consumo das mensagens:

docker exec -it <seu_nome_do_container_kafka> /opt/kafka/bin/kafka-console-consumer.sh --topic test-topic --from-beginning --bootstrap-server localhost:9092
