# Offensive ELK: Elasticsearch for Offensive Security

Offensive ELK is a custom Elasticsearch setup, aiming to show how traditional “defensive” tools can be effectively used for offensive security data analysis, helping your team collaborate and triage scan results.

In particular, Elasticsearch offers the chance to aggregate a multitude of disparate data sources, query them with a unified interface, with the aim of extracting actionable knowledge from a huge amount of unclassified data.

A full walkthrough that led me to this setup can be found at: [https://www.marcolancini.it/2018/blog-elk-for-nmap/](https://www.marcolancini.it/2018/blog-elk-for-nmap/).



# Usage

1. Clone this repository:
```
❯ git clone https://github.com/marco-lancini/docker_offensive_elk.git
```
2. Create the `_data` folder (if not present) and ensure it is owned by your own user:
```
❯ cd docker_offensive_elk/
❯ mkdir ./_data/
❯ sudo chown -R <user>:<user> ./_data/
```
3. Start the stack using docker-compose:
```
docker-elk ❯ docker-compose up -d
```
4. Give Kibana a few seconds to initialize, then access the Kibana web UI running at: http://localhost:5601.
5. Start [ingesting your nmap results](#ingest-nmap-results).
6. During the first run, [create an index](#create-an-index).



### Ingest Nmap Results

In order to be able to ingest our Nmap scans, we will have to output the results in an XML formatted report (`-oX`) that can be parsed by Elasticsearch.
Once done with the scans, place the reports in the `./_data/nmap/` folder and run the ingestor:

```bash
❯ docker-compose run ingestor
Starting elk_elasticsearch ... done
Processing /data/scan_192.168.1.0_24.xml file...
Sending Nmap data to Elasticsearch
Processing /data/scan_192.168.2.0_24.xml file...
Sending Nmap data to Elasticsearch
Processing /data/scan_192.168.3.0_24.xml file...
Sending Nmap data to Elasticsearch
```



### Create an Index

1. Open Kibana in your browser ([http://localhost:5601](http://localhost:5601)) and you should be presented with a screen similar to the one below:
![elk_index_1](.github/elk_index_1.jpg)

2. Insert `nmap*` as index pattern and press "_Next Step_":
![elk_index_2](.github/elk_index_2.jpg)

3. In the "_Time Filter_" field name choose "`time`", then click on "_Create Index Pattern_":
![elk_index_3](.github/elk_index_3.jpg)

4. If everything goes well you should be presented with a page that lists every field in the `nmap*` index and the field's associated core type as recorded by Elasticsearch. 
![elk_index_4](.github/elk_index_4.jpg)
