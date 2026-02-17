FROM apache/spark:4.0.2

USER root

RUN apt-get update && apt-get install -y \
    python3-pip \
    curl \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /opt/spark/logs /opt/spark/work /opt/spark-data/raw \
                                               /opt/spark-data/bronze \
                                               /opt/spark-data/silver \
                                               /opt/spark-data/gold \
    && chmod -R 777 /opt/spark/logs /opt/spark/work /opt/spark-data \
    && chown -R spark:spark /opt/spark/logs /opt/spark/work /opt/spark-data

ENV PYSPARK_PYTHON=/usr/bin/python3
ENV PYSPARK_DRIVER_PYTHON=/usr/bin/python3

USER spark