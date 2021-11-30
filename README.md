# rpi-tig
Dockerized Telegraf/InfluxDB/Grafana for Rpi

```
apt-get install docker.io docker-compose
```

... clone this repository, and do a single `./start.sh`. You should be set. After a couple of minutes (it's a Raspberry Pi after all), you will get the following:

- A telegraf instance gathering system stats, with statsd available on the local host for external log input
- InfluxDB storing the telegraf data
- Grafana already configured to talk to the InfluxDB instance, and preconfigured with a default system dashboard

# Included dashboards

The grafana instance is automatically provisioned with a couple of dashboard that are useful for me, and in any case are hopefully interesting examples of what grafana + influx can do.

- System stats: a Raspberry Pi centric system monitoring dashboard

# Notes

- telegraf inside a Docker container will not be able to monitor your network interfaces, obviously
- This stack works remarkably well on a Pi 3B+ (and 4, of course). I've had it monitor devices for months at a time with zero issues
- Thanks to docker-compose/Docker, the stack will survive a reboot
- Provisioned dashboards on Grafana cannot be saved, so they really should be used as templates, and saved as a new Dashboard if you want to edit/modify them
- Feel free to contribute PRs with useful dashboards if you have some
