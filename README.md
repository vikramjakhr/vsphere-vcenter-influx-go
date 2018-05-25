
# Collect VMware vCenter and ESXi performance metrics and send them to InfluxDB

# Screenshots of Grafana dashboards
![screenshot](https://grafana.com/api/dashboards/6168/images/3930/image)
![screenshot](https://grafana.com/api/dashboards/6171/images/3933/image)
![screenshot](https://grafana.com/api/dashboards/6171/images/3936/image)
![screenshot](https://grafana.com/api/dashboards/6171/images/3939/image)
![screenshot](https://grafana.com/api/dashboards/6171/images/3942/image)
![screenshot](https://grafana.com/api/dashboards/6173/images/3956/image)
![screenshot](https://grafana.com/api/dashboards/6173/images/3959/image)
![screenshot](https://grafana.com/api/dashboards/6176/images/3968/image)

# Description and Features
This is a tool written in Go that helps you do your own custom tailored monitoring, capacity planning and performance debugging of VMware based infrastructures. It collects all possible metrics from vCenters and ESXi hypervisors about hosts, clusters, resource pools, datastores and virtual machines and sends them to an [InfluxDB database](https://github.com/influxdata/influxdb) (a popular open source time series database project written in Go), which you can then visualise in Grafana (links to sample dashboards [below](#example-dashboards)) or Chronograf, and use Grafana, Kapacitor or custom scripts to do alerting based on your needs, KPIs, capacity plannings/expectations.

# Install 
Grab the [latest release](https://github.com/vikramjakhr/vsphere-vcenter-influx-go/releases/latest) 
```
wget https://github.com/vikramjakhr/vsphere-vcenter-influx-go/releases/download/v1.0.0/vsphere-vcenter-influx-go
```
