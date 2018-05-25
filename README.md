
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
Step 1: Download the [latest release](https://github.com/vikramjakhr/vsphere-vcenter-influx-go/releases/latest) by executing below command
```
wget https://github.com/vikramjakhr/vsphere-vcenter-influx-go/releases/download/v1.0.0/vsphere-vcenter-influx-go
```
Step 2: Download the config json after executing below command, and do changes related to host and influx configuration
```
wget https://github.com/vikramjakhr/vsphere-vcenter-influx-go/blob/master/vsphere-influxdb.json
```

Step 3: Now make the binary executable by running below command
```
chmod 755 vsphere-vcenter-influx-go
```

Step 4: Now move the json file into /etc by executing below command
```
mv vsphere-influxdb.json /etc
```
Step 5: Start the binary by executing below command
```
./vsphere-vcenter-influx-go
```

# Configure

The JSON configuration file in /etc/vsphere-influxdb-go.json contains all your vCenters/ESXi to connect to, the InfluxDB connection details(url, username/password, database to use), and the metrics to collect(full list [here](http://www.virten.net/2015/05/vsphere-6-0-performance-counter-description/) ).

**Note: Not all metrics are available directly, you might need to change your metric collection level.**
A table with the level needed for each metric is availble [here](http://www.virten.net/2015/05/which-performance-counters-are-available-in-each-statistic-level/), and you can find a python script to change the collect level in the [tools folder of the project](./tools/).

Additionally  you can provide a vCenter/ESXi server and InfluxDB connection details via environment variables, wich is extremly helpful when running inside a container:

For InfluxDB:
* INFLUX\_HOSTNAME
* INFLUX\_USERNAME
* INFLUX\_PASSWORD
* INFLUX\_DATABASE

For vSphere:
* VSPHERE\_HOSTNAME
* VSPHERE\_USERNAME
* VSPHERE\_PASSWORD 

Keep in mind, that currently only one vCenter/ESXi can be added via environment variable.

If you set a domain, it will be automaticaly removed from the names of the found objects.

Metrics collected are defined by associating ObjectType groups with Metric groups.

There have been reports of the script not working correctly when the time is incorrect on the vsphere or vcenter. Make sure that the time is valid or activate the NTP service on the machine.

# Run as a service

Create a crontab to run it every X minutes(one minute is fine - in our case, ~30 vCenters, ~100 ESXi and ~1400 VMs take approximately 25s to collect all metrics - rather impressive, i might add).
```
* * * * * /usr/local/bin/vsphere-influxdb-go
```

# Example dashboards
* https://grafana.com/dashboards/6168
* https://grafana.com/dashboards/6171
* https://grafana.com/dashboards/6173
* https://grafana.com/dashboards/6176

Contributions welcome!


# Compile from source

```
go get github.com/vikramjakhr/vsphere-vcenter-influx-go

```
This will install the project in your $GOBIN($GOPATH/bin). If you have appended $GOBIN to your $PATH, you will be able to call it directly. Otherwise, you'll have to call it with its full path.
Example:
```
vsphere-vcenter-influx-go
```
or :
```
$GOBIN/vsphere-vcenter-influx-go
```

# Contributing
You are welcome to contribute!