FROM python:2.7-stretch

RUN pip install --upgrade elasticsearch

ADD VulntoES /opt/VulntoES
ADD ingest /bin/ingest
WORKDIR /opt/VulntoES

CMD ["/bin/bash"]