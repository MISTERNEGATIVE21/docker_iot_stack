# docker_iot_stack
Docker Compose File for IOT (ESP8266 and ESP32)
# Docker Compose Setup

This Docker Compose configuration sets up a local environment with MQTT, Grafana, InfluxDB, and Visual Studio Code. It allows you to quickly run and configure these services for your development needs.

## Services

### MQTT

- Image: eclipse-mosquitto
- Container Name: mqtt
- Port Mapping: 1883:1883

An MQTT broker is set up using the eclipse-mosquitto image. The broker is accessible on port 1883.

### Grafana

- Image: grafana/grafana
- Container Name: grafana
- Port Mapping: 3000:3000
- Environment Variables:
  - GF_INSTALL_PLUGINS=grafana-clock-panel,grafana-simple-json-datasource
  - GF_AUTH_ANONYMOUS_ENABLED=true

Grafana, a data visualization tool, is set up using the grafana/grafana image. It is accessible on port 3000. The environment variables enable additional plugins and allow anonymous access.

### InfluxDB

- Image: influxdb
- Container Name: influxdb
- Port Mapping: 8086:8086
- Environment Variables:
  - INFLUXDB_DB=mydb
  - INFLUXDB_ADMIN_USER=admin
  - INFLUXDB_ADMIN_PASSWORD=admin
  - INFLUXDB_USER=user
  - INFLUXDB_USER_PASSWORD=user

InfluxDB, a time-series database, is set up using the influxdb image. It is accessible on port 8086. The environment variables configure the database name and set up administrator and user credentials.

### Visual Studio Code (VSCode)

- Image: codercom/code-server:latest
- Container Name: vscode
- Port Mapping: 8080:8080
- Volumes: ./vscode:/home/coder/project
- Environment Variables:
  - PASSWORD=your_password
- Devices:
  - /dev/ttyACM0:/dev/ttyACM0
  - /dev/ttyUSB0:/dev/ttyUSB0
- Privileged: true

Visual Studio Code (VSCode) is set up using the codercom/code-server image. It is accessible on port 8080. The project directory is mounted as a volume, allowing you to work on your code. The PASSWORD environment variable sets the password for accessing the VSCode instance. Additionally, the devices configuration enables access to USB devices such as /dev/ttyACM0 and /dev/ttyUSB0, which can be useful for Arduino development. The privileged flag is set to true to provide necessary permissions.

## Usage

1. Install Docker and Docker Compose if you haven't already.

2. Clone or download this repository to your local machine.

3. In a terminal, navigate to the directory containing the docker-compose.yml file.

4. Run the following command to start the services:

   ```bash
   docker-compose -d up
