# The Horizontal Scaling Solution
By running 

```bash
docker-compose -f docker-compose-worker.yml up -d
```
on any amount of workers and 

```bash
docker-compose -f docker-compose-master.yml up -d
```
on the master vm, you can start the horizontal scaling solution.

Log in to the containers and check the pyspark versions and makesure all are compatible. (Set JAVA_HOME if it is not exported)

```bash
sudo docker exec -u 0 -it <container id or name> /bin/bash
```
Run 
```bash
pip list
```
If there's a version mismatch install the matching pyspark version (since we are using images with latest tags they can be changed)
```bash
pip install pyspark==<version>
```

Got the master connected to the worker on separate and the spark cluster can work independently without hadoop. It successfully create executors on spark workers and process the data the job finish properly. The hadoop is up and we were able to upload data to the multi-node hadoop cluster. 

Added jupyter notebook contains test script with results cells which is used to test the sprak clusture on multiple VMs (Horizontal scaling.) 