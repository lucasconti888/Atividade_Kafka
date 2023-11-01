# Atividade_Kafka

## Arquivo YML

O arquivo YML criado aqui contém os seguintes serviços: o zookeper, com os parâmetros image e ports; o kafka-manager, com os parâmetros image, ports e environment (onde é definido o "ZK_HOSTS" que o conecta ao zookeper); e o kafka, com image, ports, expose e environment, este último com as seguintes configurações definidas:

![image](https://github.com/lucasconti888/Atividade_Kafka/assets/99270135/c1272e46-9482-4d19-bbf0-134c65836199)

KAFKA_CREATE_TOPICS define que deve ser criado um tópico assim que o container se inicia. 

KAFKA_ADVERTISED_LISTENERS, KAFKA_LISTENER_SECURITY_PROTOCOL_MAP, KAFKA_LISTENERS e KAFKA_INTER_BROKER_LISTENER_NAME são variáveis de ambiente que foram setadas com os valores específicos para o funcionamento no ambiente local.

KAFKA_ZOOKEEPER_CONNECT conecta o kafka ao zookeper.

## Terminal

### Após a criação do arquivo yml, é preciso ativar o docker (em alguns casos é feito abrindo o docker desktop) e então rodar o docker-compose na respectiva pasta com o seguinte comando:

docker-compose up -d

### Após isso, o seguinte comando permite que o usuário visualize o nome do container kafka criado:

docker ps

### O seguinte comando permite a criação de um tópico e deve retornar um erro no terminal, uma vez que o serviço do kafka foi configurado para iniciar um tópico de maneira automática:

docker exec -it <nome_do_container_kafka> /opt/kafka/bin/kafka-topics.sh --create --topic test-topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

### Por fim, em um terminal pode ser feita a produção de mensagens:

docker exec -it <seu_nome_do_container_kafka> /opt/kafka/bin/kafka-console-producer.sh --topic test-topic --bootstrap-server localhost:9092

![image](https://github.com/lucasconti888/Atividade_Kafka/assets/99270135/eaf69fe9-622d-4953-8295-091201cbe825)

### Em outro, pode ser feita a visualização ou o consumo das mensagens:

docker exec -it <seu_nome_do_container_kafka> /opt/kafka/bin/kafka-console-consumer.sh --topic test-topic --from-beginning --bootstrap-server localhost:9092

![image](https://github.com/lucasconti888/Atividade_Kafka/assets/99270135/9e3be8e1-bab2-440d-99a4-2020d7dda513)


