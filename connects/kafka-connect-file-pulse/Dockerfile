# ==================================================
# Kafka Connect Image para OpenShift Container Platform
# Incluye conector: FilePulse (SFTP)
# ==================================================

FROM quay.io/strimzi/kafka:0.45.0-kafka-3.8.0

# Metadatos de la imagen
LABEL io.strimzi.kafka-version="3.8.0"
LABEL strimzi.io/kind="KafkaConnect"
LABEL maintainer="Equipo Operaciones - Fabrica Digital Claro Colombia"
LABEL description="Kafka Connect con FilePulse para SFTP"
LABEL version="1.0.0"

USER root

# ==================================================
# Crear directorios para plugins
# ==================================================
RUN mkdir -p /opt/kafka/plugins/filepulse

# ==================================================
# CONECTOR FILEPULSE (para SFTP)
# Descargar la versión más reciente compatible: v2.15.0
# ==================================================
RUN curl -L https://github.com/streamthoughts/kafka-connect-file-pulse/releases/download/v2.15.0/streamthoughts-kafka-connect-file-pulse-2.15.0.zip \
  -o /tmp/streamthoughts-kafka-connect-file-pulse-2.15.0.zip && \
  unzip /tmp/streamthoughts-kafka-connect-file-pulse-2.15.0.zip -d /tmp/ && \
  cp /tmp/streamthoughts-kafka-connect-file-pulse-2.15.0/lib/*.jar /opt/kafka/plugins/filepulse/ && \
  rm -rf /tmp/streamthoughts-kafka-connect-file-pulse*

# ==================================================
# CONFIGURACIÓN DE PERMISOS Y LIMPIEZA
# ==================================================
RUN chown -R 1001:1001 /opt/kafka/plugins && \
  chmod -R 755 /opt/kafka/plugins

# Limpiar archivos temporales
RUN rm -rf /tmp/*

USER 1001

# ==================================================
# INFORMACIÓN DE LA IMAGEN
# ==================================================
# Para verificar los plugins instalados, ejecutar:
RUN ls -la /opt/kafka/plugins/filepulse/