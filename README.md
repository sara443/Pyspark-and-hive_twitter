# spark-and-hive-pipeline
This project have 5 scripts: 

1- Twitter_listener :
This code is designed to send GET requests to the Twitter API to retrieve recent tweets related to a 
specific keyword ("Immigration”) and within a specific time range. It uses the requests library to send the 
API requests and retrieve the JSON responses. The code then parses the response data, extracts relevant 
information such as tweet text, creation time, and tweet ID, and encodes them in UTF-8 format.
The code also creates a socket and listens for incoming connections on a specified port. Once a 
connection is established, it iterates over the tweet data and sends each tweet's information as a JSON 
string to the connected socket. The code includes a sleep interval of 2 seconds between sending each 
tweet to avoid overwhelming the receiving end  demonstrates a PySpark streaming pipeline for processing and storing tweets received 
from a socket connection. 

2- Twitter stream:
a PySpark streaming pipeline for processing and storing tweets received 
from a socket connection.
Every time I run I take the data from spark stream into a parquet file in HDFS in (append mode) .
And also I take the data from spark stream and save it in HIVE in a landing table in (overwrite mode) to 
just save the newest data only every time. And then the data goes to the dimensions and it saved there.
Note : I did not make truncate for the data in the landing table because it has the newest data only ,it 
overwrites the data in it every time we run … and this will reduce time in inserting the data every time .

3- HIVE Script:
This code focus on creating two Hive tables: tweet_dim and tweet_properties.

4- SparkSQL Script:
this code performs data processing operations, including joining, filtering, and 
aggregating data from the previously created Hive tables, and then saves the processed data as fact 
tables in a new database at (HIVE) for further analysis and querying.

5- Run all Script:
This code runs four different scripts using the subprocess module
