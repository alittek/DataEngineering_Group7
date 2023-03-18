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

Got the master connected to the worker on separate VMs but I can't send work to the worker from jupyter notebook. I can see the worker in the master's dashboard but I can't send work to it. I've tried the following:

```python
from pyspark.sql import SparkSession
import socket

driver_ip = socket.gethostbyname(socket.gethostname())

spark = SparkSession.builder \
    .appName("Pi Calculation") \
    .master("spark://192.168.2.107:7077") \
    .config("spark.cores.max", 1) \
    .config("spark.executor.memory", "1024m") \
    .config("spark.driver.host", f"{driver_ip}") \
    .getOrCreate()

sc = spark.sparkContext

import random

num_samples = 100000

def inside(p):
    x, y = random.random(), random.random()
    return x * x + y * y < 1

count = sc.parallelize(range(0, num_samples)).filter(inside).count()
pi = 4 * count / num_samples
print("Pi is roughly", pi)
sc.stop()
```