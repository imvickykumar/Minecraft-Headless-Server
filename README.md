# `Setup Bedrock Server`

* Start the server on boot automatically
* Easily start, stop, restart with simple commands
* Run the server in the background without needing `screen` or `tmux`
* Manage logs more cleanly

---

### Here's how to create a systemd service for your Bedrock server:

1. **Create the service file**

Run:

```bash
sudo nano /etc/systemd/system/bedrock.service
```

Paste the following, adjust paths if needed:

```ini
[Unit]
Description=Minecraft Bedrock Server
After=network.target

[Service]
WorkingDirectory=/root/projects/bedrock-server
ExecStart=/root/projects/bedrock-server/bedrock_server
Restart=always
RestartSec=10
User=root
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
```

2. **Reload systemd to apply the new service**

```bash
sudo systemctl daemon-reload
```

3. **Start the Bedrock server service**

```bash
sudo systemctl start bedrock.service
```

4. **Check status/logs**

```bash
sudo systemctl status bedrock.service
```

```bash
sudo journalctl -u bedrock.service -f
```

5. **Enable it to start on boot**

```bash
sudo systemctl enable bedrock.service
```

---

### Useful commands once service is created:

* Start server:
  `sudo systemctl start bedrock.service`

* Stop server:
  `sudo systemctl stop bedrock.service`

* Restart server:
  `sudo systemctl restart bedrock.service`

* See logs live:
  `sudo journalctl -u bedrock.service -f`

---

### Let’s install the Playit agent manually instead — it’s straightforward:

1. Download the latest Linux binary:

```bash
wget https://github.com/playit-cloud/playit-agent/releases/latest/download/playit-linux-amd64
```

2. Make it executable:

```bash
chmod +x playit-linux-amd64
```

3. Move it to a directory in your PATH:

```bash
sudo mv playit-linux-amd64 /usr/local/bin/playit
```

4. Now you can run:

```bash
playit
```

