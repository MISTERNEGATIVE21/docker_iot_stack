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
## Install PlatformIo Tools

Follow these steps to install PlatformIO in Visual Studio Code:

1. Download and install Visual Studio Code from the official website: [https://code.visualstudio.com/](https://code.visualstudio.com/)

2. Launch Visual Studio Code.

3. Open the Extensions view by clicking on the square icon on the left sidebar or pressing `Ctrl+Shift+X`.

4. In the search bar, type "PlatformIO" and press Enter.

5. Look for the "PlatformIO IDE" extension in the search results and click the "Install" button.

6. Once the installation is complete, click the "Reload" button to activate the extension.

7. After the reload, you should see the PlatformIO icon on the left sidebar of Visual Studio Code.

## Getting Started

To create a new PlatformIO project, follow these steps:

1. Click on the PlatformIO icon on the left sidebar to open the PlatformIO Home.

2. Click on the "New Project" button.

3. Select the board you are using for your project from the list or enter the board name in the search box.

4. Choose the framework you want to use (e.g., Arduino, ESP-IDF, etc.).

5. Enter a name for your project and select a location to save it.

6. Click on the "Finish" button to create the project.

7. The project will be initialized, and the necessary files and folders will be created.

## Building and Uploading Code

To build and upload your code to the target device, follow these steps:

1. Open your PlatformIO project in Visual Studio Code.

2. Open the terminal by clicking on "View" in the top menu and selecting "Terminal" or by pressing `Ctrl+` backtick.

3. Use the following commands in the terminal:

   - Build the project: `pio run`
   - Upload the code to the device: `pio run --target upload`

   You can also use the PlatformIO toolbar on the left sidebar for build and upload actions.

## Additional Resources

- [PlatformIO Documentation](https://docs.platformio.org/)
- [Visual Studio Code Documentation](https://code.visualstudio.com/docs)
- [PlatformIO Official Website](https://platformio.org/)


