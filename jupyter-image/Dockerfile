FROM python:3.10-slim

USER root

# Java requis pour PySpark
RUN apt-get update && apt-get install -y \
    default-jdk \
    curl \
    && rm -rf /var/lib/apt/lists/*

# JupyterLab + PySpark + librairies data
RUN pip install --no-cache-dir \
    jupyterlab==4.3.6 \
    pyspark==4.0.2 \
    notebook \
    ipykernel \
    pandas \
    pyarrow

# Utilisateur sory
RUN useradd -m -u 1000 -s /bin/bash sory \
    && mkdir -p /home/sory/work/app \
               /home/sory/work/data \
               /home/sory/work/notebooks \
    && chmod -R 777 /home/sory/work \
    && chown -R sory:sory /home/sory

WORKDIR /home/sory/work
USER sory

EXPOSE 8888

CMD ["jupyter", "lab", \
     "--ip=0.0.0.0", \
     "--port=8888", \
     "--no-browser", \
     "--NotebookApp.token=", \
     "--NotebookApp.password="]