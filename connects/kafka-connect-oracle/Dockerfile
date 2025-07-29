FROM quay.io/strimzi/kafka:0.45.0-kafka-3.8.0

LABEL io.strimzi.kafka-version="3.8.0"
LABEL strimzi.io/kind="KafkaConnect"

USER root

RUN mkdir -p /opt/kafka/plugins/jdbc

COPY kafka-connect-jdbc-10.8.2.jar /opt/kafka/plugins/jdbc/

COPY libs/ojdbc8.jar /opt/kafka/plugins/jdbc/

USER 1001