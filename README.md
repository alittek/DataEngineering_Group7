# DataEngineering_Group7

## Data Uploading
To upload data to HDFS, use the following command, change the dates as needed:

```bash
wget -qO- https://files.pushshift.io/reddit/comments/RC_2011-08.zst | zstd --long=31 -d --stdout - | docker exec -i hadoop-namenode hdfs dfs -put - /reddit/RC_2011-08.json
```

This will download the data from the pushshift.io website, decompress it, and upload it to HDFS, all without storing anything in the middle as it is streamed. The data is stored in the `/reddit` directory on HDFS.