ARG REGISTRY_URL
FROM ${REGISTRY_URL}grafana/grafana:9.3.2-ubuntu

USER root

RUN apt-get update && apt-get install -y procps gettext-base && rm -rf /var/lib/apt/lists/*

WORKDIR /etc/grafana

COPY datasources ./datasources
COPY dashboard/dashboards.yaml /etc/grafana/provisioning/dashboards
COPY dashboard/gatling-dashboard.json /etc/grafana/provisioning/dashboards
COPY dashboard/grafana-report_rev3.json /etc/grafana/provisioning/dashboards
COPY dashboard/gatling-report-trend2.json /etc/grafana/provisioning/dashboards


WORKDIR /app
COPY entrypoint.sh ./
RUN chmod u+x entrypoint.sh

ENTRYPOINT ["/app/entrypoint.sh"]