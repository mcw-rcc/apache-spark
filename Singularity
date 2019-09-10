Bootstrap: docker
From: ubuntu:18.04

%labels
  Maintainer Matthew Flister
  Spark 2.4.4
  Hadoop 2.7

%help
  This container will run Apache Spark.

%environment
  export SPARK_HOME=/opt/spark
  export PATH=${SPARK_HOME}/bin:${PATH}

%post
  export SPARK_VERSION=2.4.4
  export HADOOP_VERSION=2.7

  mkdir -p /scratch/global /scratch/local /rcc/stor1/refdata /rcc/stor1/projects /rcc/stor1/depts

  apt-get update
  apt-get install -y --no-install-recommends \
    openjdk-8-jre \
    python \
    python3 \
    python-dev \
    python3-dev \
    python-setuptools \
    python3-setuptools \
    python-pip \
    python3-pip \
    wget
  
  # install python packages
  pip install --no-binary --upgrade \
    wheel \
    numpy \
    scipy \
    jupyter \
    pandas \
    pyspark

  pip3 install --no-binary --upgrade \
    wheel \
    numpy \
    scipy \
    jupyter \
    jupyterhub \
    pandas \
    pyspark

  #install spark
  mkdir -p /opt/spark
  wget http://mirrors.sonic.net/apache/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz
  tar -xzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz -C /opt/spark --strip-components=1

  rm -rf /var/lib/apt/lists/*
