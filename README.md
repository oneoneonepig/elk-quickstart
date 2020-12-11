# ELK using docker-compose with examples

- Use `docker-compose.yml` to start Elasticsearch and Kibana service
   - The containers used fixed named like "elasticsearch" and "kibana" to simplify the dns name

### Parsing Windows NPS Radius Log (dts compliant)

1. `cd windows-nps`
1. Place the log file (e.g. IN20200101.txt) in the `example/` directory
1. Change the log file extension to `.xml` in order to be parsed by logstash. For exmaple, `mv IN20200101.txt IN20200101.xml`
1. Run the following command to parse the log file and store it in Elasticsearch (there is a `test.xml` file for demostration)
    ```
    docker run -d --rm --net elk-quickstart_elk \
    -v $(pwd)/logstash.conf:/usr/share/logstash/pipeline/logstash.conf \
    -v $(pwd)/example:/tmp docker.elastic.co/logstash/logstash:7.10.0
    ```
1. Create the `Kibana Index Pattern` in order to view the log data in Discover

### Parsing Tomcat Access Log

1. `cd tomcat`
1. Place the log file (e.g. localhost_access_log.2020-11-20.txt) in the `example/` directory
1. Make sure the log file has `.txt` extension
1. Run the following command to parse the log file and store it in Elasticsearch
     ```
     docker run -d --rm --net elk-quickstart_elk \
     -v $(pwd)/logstash.conf:/usr/share/logstash/pipeline/logstash.conf \
     -v $(pwd)/example:/tmp docker.elastic.co/logstash/logstash:7.10.0
     ```
1. Create the `Kibana Index Pattern` in order to view the log data in Discover

### Parsing DNS Host File

1. `cd dns`
1. Place the log file (e.g. domain.hosts) in the `example/` directory
1. Make sure the log file has `.hosts` extension
1. Run the following command to parse the host file and store it in Elasticsearch
     ```
     docker run -d --rm --net elk-quickstart_elk \
     -v $(pwd)/logstash.conf:/usr/share/logstash/pipeline/logstash.conf \
     -v $(pwd)/example:/tmp docker.elastic.co/logstash/logstash:7.10.0
     ```
1. Create the `Kibana Index Pattern` in order to view the log data in Discover
