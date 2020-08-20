# ELK for parsing Windows NPS Radius Log (dts compliant)

1. Use `docker-compose.yml` to start Elasticsearch and Kibana service
   - The containers used fixed named like "elasticsearch" and "kibana" to simplify the dns name
1. Place the log file (e.g. IN20200101.txt) in the `logstash/logs/` directory
1. Change the log file extension to `.xml` in order to be parsed by logstash `mv IN20200101.txt IN20200101.xml`
1. Run the following command to parse the log file and store it in Elasticsearch (there is a test.xml file as an example)
```
docker run -d --rm --net elk-windows-radius-log_elk -v $(pwd)/logstash/logstash.conf:/usr/share/logstash/pipeline/logstash.conf -v $(pwd)/logstash/logs:/tmp docker.elastic.co/logstash/logstash:7.9.0
```
1. Create the Kibana Index Pattern in order to view the log data in Discover
