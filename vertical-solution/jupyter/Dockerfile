ARG debian_buster_image_tag=8-jre-slim
FROM openjdk:${debian_buster_image_tag}

ARG scala_version="2.12.10"
ARG build_date
ARG shared_workspace=/opt/workspace

RUN mkdir -p ${shared_workspace}/data
RUN mkdir -p /usr/share/man/man1
RUN apt-get update -y
RUN apt-get install -y curl python3 r-base
RUN ln -s /usr/bin/python3 /usr/bin/python

ENV SHARED_WORKSPACE=${shared_workspace}

VOLUME ${shared_workspace}
CMD ["bash"]

ARG build_date

#JupyterLab + Python kernel for PySpark
COPY workspace/ /workspace/

RUN apt-get update -y
RUN apt-get install -y python3-pip python3-dev
RUN pip3 install --upgrade pip
RUN pip3 install wget==3.2 pyspark==3.0.0 jupyterlab
RUN pip3 install pandas
RUN pip3 install matplotlib
RUN pip3 install pyspark_dist_explore
RUN pip3 install dataframe_image
RUN pip3 install numpy

EXPOSE 8888

WORKDIR /workspace
CMD jupyter lab --ip=0.0.0.0 --port=8888 --no-browser --allow-root --NotebookApp.token=
