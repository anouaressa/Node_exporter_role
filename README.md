# The steps for instaling node exporte:



# Node exporter : installation binaire

* preparation 

```
sudo useradd -rs /bin/false node_exporter
https://prometheus.io/download/#node_exporter
wget https://github.com/prometheus/node_exporter/releases/download/v0.18.1/node_exporter-0.18.1.linux-amd64.tar.gz
tar -xvzf node_exporter-0.18.1.linux-amd64.tar.gz
mv node_exporter-0.18.1.linux-amd64/node_exporter /usr/local/bin/
chown node_exporter:node_exporter /usr/local/bin/node_exporter
```

* systemd : /etc/systemd/system/node_exporter.service

```
[Unit]
Description=Node Exporter
After=network-online.target
[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter
[Install]
WantedBy=multi-user.target
```

```
systemctl daemon-reload
systemctl enable node_exporter
systemctl start node_exporter
```
