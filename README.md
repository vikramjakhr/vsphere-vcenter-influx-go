
# Collect VMware vCenter and ESXi performance metrics and send them to InfluxDB

# Screenshots of Grafana dashboards
![screenshot](https://grafana.com/api/dashboards/3556/images/2224/image)
![screenshot](https://grafana.com/api/dashboards/3556/images/2227/image)
![screenshot](https://grafana.com/api/dashboards/3556/images/2230/image)
![screenshot](https://grafana.com/api/dashboards/3571/images/2245/image)
![screenshot](https://grafana.com/api/dashboards/3571/images/2251/image)
![screenshot](https://grafana.com/api/dashboards/3571/images/2254/image)

# Description and Features
This is a tool written in Go that helps you do your own custom tailored monitoring, capacity planning and performance debugging of VMware based infrastructures. It collects all possible metrics from vCenters and ESXi hypervisors about hosts, clusters, resource pools, datastores and virtual machines and sends them to an [InfluxDB database](https://github.com/influxdata/influxdb) (a popular open source time series database project written in Go), which you can then visualise in Grafana (links to sample dashboards [below](#example-dashboards)) or Chronograf, and use Grafana, Kapacitor or custom scripts to do alerting based on your needs, KPIs, capacity plannings/expectations.
