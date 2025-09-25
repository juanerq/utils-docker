FROM quay.io/strimzi/kafka:0.46.0-kafka-4.0.0

LABEL io.strimzi.kafka-version="4.0.0"
LABEL strimzi.io/kind="KafkaConnect"

USER root

RUN install -d -m 0775 -o 1001 -g 0 /opt/kafka/plugins/jdbc \
  && curl -fSL "https://packages.confluent.io/maven/io/confluent/kafka-connect-jdbc/10.8.2/kafka-connect-jdbc-10.8.2.jar" \
  -o /opt/kafka/plugins/jdbc/kafka-connect-jdbc-10.8.2.jar \
  && curl -fSL "https://packages.confluent.io/maven/io/confluent/kafka-connect-jdbc/10.8.2/kafka-connect-jdbc-10.8.2.jar.sha1" \
  -o /tmp/kcj.sha1 \
  && test "$(sha1sum /opt/kafka/plugins/jdbc/kafka-connect-jdbc-10.8.2.jar | awk '{print $1}')" = "$(cat /tmp/kcj.sha1)" \
  && rm -f /tmp/kcj.sha1

RUN curl -fSL "https://repo1.maven.org/maven2/com/oracle/database/jdbc/ojdbc11/23.9.0.25.07/ojdbc11-23.9.0.25.07.jar" \
  -o /opt/kafka/plugins/jdbc/ojdbc11.jar

USER 1001
