FROM registry.redhat.io/ubi8/ubi:latest

RUN dnf install -y wget 
RUN wget https://github.com/prometheus/prometheus/releases/download/v2.18.1/prometheus-2.18.1.linux-amd64.tar.gz -O /prometheus-2.18.1.linux-amd64.tar.gz 

RUN tar -xvf /prometheus-2.18.1.linux-amd64.tar.gz 

EXPOSE 9090

WORKDIR /prometheus-2.18.1.linux-amd64/

CMD /prometheus-2.18.1.linux-amd64/prometheus --config.file=/etc/prometheus/prometheus.yml
