FROM docker.elastic.co/elasticsearch/elasticsearch:5.6.9

RUN bin/elasticsearch-plugin install analysis-icu

COPY --chown=elasticsearch:elasticsearch elasticsearch.yml /usr/share/elasticsearch/config/
COPY --chown=elasticsearch:elasticsearch jvm.options /usr/share/elasticsearch/config/

EXPOSE 9200 9300