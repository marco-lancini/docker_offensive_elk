FROM python:3.7-stretch

ADD ./requirements.txt /tmp/requirements.txt
RUN pip install --upgrade -r /tmp/requirements.txt

WORKDIR /opt/VulntoES
ADD ./VulntoES.py /opt/VulntoES/
ADD ./ingest /opt/VulntoES/

CMD ["/opt/VulntoES/ingest"]