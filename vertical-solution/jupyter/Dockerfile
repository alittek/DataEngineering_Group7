FROM andreper/jupyterlab
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update -y
RUN apt-get install -y python3-pip python3-dev
RUN pip3 --timeout=1000 install --upgrade pip
RUN pip3 --timeout=1000 install wget==3.2 
RUN pip3 --timeout=1000 install pyspark==${spark_version}
RUN pip3 --timeout=1000 install pandas
