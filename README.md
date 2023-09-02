# The steps for instaling node exporte:



# Node exporter : installation binaire


Download Node Exporter binary from the specified URL.
Extract the downloaded binary to /usr/local/bin.
Create a system user called node_exporter with the /bin/false shell.
Set ownership of the Node Exporter binary to the node_exporter user and group.
Copy the systemd service template to the /etc/systemd/system directory.
Notify the systemd handler to reload systemd configuration after copying the service file.
Enable and start the Node Exporter systemd service.

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
