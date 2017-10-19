# Install flume-source

1.  Download `flume-sources-1.0-SNAPSHOT.jar` from this [link](https://www.dropbox.com/s/qvudqfym5givwdg/flume-sources-1.0-SNAPSHOT.jar?dl=0).

2.  Copy the downloaded `flume-sources-1.0-SNAPSHOT.jar` to the Flume classpath
    Copy `flume-sources-1.0-SNAPSHOT.jar` to 

    ``` 
    /usr/lib/flume-ng/plugins.d/twitter-streaming/lib/flume-sources-1.0-SNAPSHOT.jar
    ```

    ```
    /usr/lib/flume-ng/lib/lume-sources-1.0-SNAPSHOT.jar
    ```

    ```
    /var/lib/flume-ng/plugins.d/twitter-streaming/lib/flume-sources-1.0-SNAPSHOT.jar
    ```
    if those places don't exist, `sudo mkdir` them.

3.  Edit (or create) `/root/flume/conf/flume-twitter.conf` file to be like shown below.

    ```
    TwitterAgent.sources = Twitter
    TwitterAgent.channels = MemChannel
    TwitterAgent.sinks = HDFS
    TwitterAgent.sources.Twitter.type = com.cloudera.flume.source.TwitterSource
    TwitterAgent.sources.Twitter.channels = MemChannel
    TwitterAgent.sources.Twitter.consumerKey = YourConsumerKey
    TwitterAgent.sources.Twitter.consumerSecret = YourConsumerSecret
    TwitterAgent.sources.Twitter.accessToken = YourAccessToken
    TwitterAgent.sources.Twitter.accessTokenSecret = YourAccessTokenSecret
    TwitterAgent.sources.Twitter.keywords = hadoop, big data, analytics, bigdata, cloudera, data science, data scient$
    TwitterAgent.sinks.HDFS.channel = MemChannel
    TwitterAgent.sinks.HDFS.type = hdfs
    TwitterAgent.sinks.HDFS.hdfs.path = hdfs:///user/flume/tweets/
    TwitterAgent.sinks.HDFS.hdfs.fileType = DataStream
    TwitterAgent.sinks.HDFS.hdfs.writeFormat = Text
    TwitterAgent.sinks.HDFS.hdfs.batchSize = 1000
    TwitterAgent.sinks.HDFS.hdfs.rollSize = 0
    TwitterAgent.sinks.HDFS.hdfs.rollCount = 10000
    TwitterAgent.channels.MemChannel.type = memory
    TwitterAgent.channels.MemChannel.capacity = 10000
    TwitterAgent.channels.MemChannel.transactionCapacity = 100
    ```

4. Run this command.
    ``` bash
    flume-ng agent --name TwitterAgent --conf /root/flume/conf --conf-file /root/flume/conf/flume-twitter.conf
    ```

# Install hive json serde

1.  Download json-serde from this [link](http://www.congiu.net/hive-json-serde/1.3.8/cdh5/json-serde-1.3.8-jar-with-dependencies.jar).

2.  And copy it to `/usr/lib/hive/lib/` or use `ADD JAR` in Hive.

3.  Then, run `hive` and enter this command to create a table from data which created by flume.

    ```
    CREATE EXTERNAL TABLE tweets (
    id BIGINT,
    created_at STRING,
    source STRING,
    favorited BOOLEAN,
    retweet_count INT,
    retweeted_status STRUCT<
    text:STRING,
    `user`:STRUCT<screen_name:STRING,name:STRING>>,
    entities STRUCT<
    urls:ARRAY<STRUCT<expanded_url:STRING>>,
    user_mentions:ARRAY<STRUCT<screen_name:STRING,name:STRING>>,
    hashtags:ARRAY<STRUCT<text:STRING>>>,
    text STRING,
    `user` STRUCT<
    screen_name:STRING,
    name:STRING,
    friends_count:INT,
    followers_count:INT,
    statuses_count:INT,
    verified:BOOLEAN,
    utc_offset:INT,
    time_zone:STRING>,
    in_reply_to_screen_name STRING
    )
    ROW FORMAT SERDE "org.openx.data.jsonserde.JsonSerDe"
    LOCATION "/user/flume/tweets";
    ```

4. And the table will be created. However, enter this command in hive to make sure that the table has been created correctly.

    ``` SQL
    select * from tweets;
    ```