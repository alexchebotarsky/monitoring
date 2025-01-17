# Grafana monitoring

### Installation

- Add custom systemctl service in `/etc/systemd/system/grafana.service`:

  ```
  [Unit]
  Description=Grafana
  After=network.target docker.service
  Requires=docker.service

  [Service]
  Type=simple
  User=USER_NAME_HERE
  WorkingDirectory=/path/to/grafana
  ExecStart=docker compose up
  ExecStop=docker compose down
  Restart=on-failure

  [Install]
  WantedBy=multi-user.target
  ```

  > Remember to replace `/path/to` with an actual path to the project

  Then enable the service to run on startup:

  ```
  sudo systemctl enable grafana.service
  ```
