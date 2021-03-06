# Installing Trellis

## Requirements

  * Java 8 or later

## Installation

To install Trellis as a systemd service on linux, follow these steps:

1. Move the unpacked Trellis directory to a location such as `/opt/trellis`.
   If you choose a different location, please update the `./etc/trellis-db.service` script.

2. Edit the `./etc/environment` file as desired (optional).

3. Edit the `./etc/config.yml` file as desired. The database connection MUST be configured.

4. Create a trellis user:

        $ sudo useradd -r trellis -s /sbin/nologin

5. Create data directories

        $ sudo mkdir /opt/trellis/data
        $ sudo chown trellis.trellis /opt/trellis/data

6. Install the systemd file:

        $ sudo systemctl link /opt/trellis/etc/trellis-db.service

7. Reload systemd to see the changes

        $ sudo systemctl daemon-reload

8. Start the trellis service

        $ sudo systemctl start trellis-db

To check that trellis is running, check the URL: `http://localhost:8080`

Application health checks are available at `http://localhost:8081/healthcheck`
