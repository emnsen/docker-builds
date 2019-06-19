FROM blacktop/elasticsearch:5.6

LABEL maintainer="emin şen"
LABEL maintainer.author="contact@emnsen.com"

RUN bin/elasticsearch-plugin install analysis-icu

COPY --chown=elasticsearch:elasticsearch elasticsearch.yml /usr/share/elasticsearch/config/
COPY --chown=elasticsearch:elasticsearch jvm.options /usr/share/elasticsearch/config/

EXPOSE 9200 9300