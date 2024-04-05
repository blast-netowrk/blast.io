How to install a blast web proxy engine.


1. Download the blast executable file
2. mv your executable file to binary path
3. Options
   -f target to specific config file
   -Dlogback.configurationFile=<YOUR_LOG_FILE>
5. Create a Systemd service file sample below.

  ```sh

[Unit]
Description=blast - highest quality performance web server
Documentation=https://blast.io
After=network-online.target remote-fs.target nss-lookup.target
Wants=network-online.target

[Service]
Type=simple
PIDFile=/var/run/blast.pid
ExecStart=/usr/local/bin/blast -f /etc/blast/blast-config.yaml -Dlogback.configurationFile=/etc/blast/logback.xml
ExecStop=/bin/kill -s TERM $MAINPID

[Install]
WantedBy=multi-user.target

  ```
6. sudo systemctl daemon-reload
7. start the blast service

### Enable the admin to reload the service with zero down time

```yaml
enableAdmin: true
...
```
1. reload the service by trigger

```bash

curl http://localhost:3568/_reload

```

2. Retrieve the license status and validity info

```bash

curl http://localhost:3568/_reload

```
