FROM sebp/elk

ENV ES_HOME /opt/elasticsearch

WORKDIR ${ES_HOME}

RUN CONF_DIR=/etc/elasticsearch gosu elasticsearch bin/elasticsearch-plugin \
    install -b ingest-geoip

RUN CONF_DIR=/etc/elasticsearch gosu elasticsearch bin/elasticsearch-plugin \
    install -b ingest-user-agent

COPY logstash/30-output.conf /etc/logstash/conf.d/30-output.conf

COPY logstash/02-beats-input.conf /etc/logstash/conf.d/02-beats-input.conf

COPY logstash/10-syslog.conf /etc/logstash/conf.d/10-syslog.conf

