Follow these steps to reproduce the work we have done.

1. Clone the repository

2. Navigate inside vertical solution folder

3. Since we were doing multiple builds to fix issues, try things we downloaded hadoop to the VM and then copy it to the docker context
    - Download hadoop, unzip and move the hadoop-3.3.4 folder to hadoop/base folder
    Or
    - Add wget <hadoop path> unzip commands and relevant command to move the folder easily by changing hadoop/base/Dockerfile

4. Run 
```bash
sudo sh master-build.sh
```

Once the build is completed the spark clusture will be up and running.
use public_IP:8080 to access Spark UI
use public_IP:9870 to access Hadoop UI
use public_IP:8888 to access Jupyter labs

Then you can use the given data upload command to upload data files to hdfs. (We are using pipes and directly uploading data to the HDFS) and then use the scripts in experiments to connect to the cluster and 
