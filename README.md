# Go-Raspi-Temp-Monitor 🌡️

![GitHub release](https://img.shields.io/github/release/Sumadipraja/go-raspi-temp-monitor.svg) ![GitHub issues](https://img.shields.io/github/issues/Sumadipraja/go-raspi-temp-monitor.svg) ![GitHub stars](https://img.shields.io/github/stars/Sumadipraja/go-raspi-temp-monitor.svg)

Go-Raspi-Temp-Monitor is a temperature monitoring application designed for Raspberry Pi devices. This application reads the CPU temperature at regular intervals and sends alerts via email when the temperature exceeds a specified threshold. 

You can download the latest version of the application from the [Releases section](https://github.com/Sumadipraja/go-raspi-temp-monitor/releases). Make sure to download the appropriate file for your Raspberry Pi model and execute it to get started.

## Table of Contents

1. [Features](#features)
2. [Installation](#installation)
3. [Usage](#usage)
4. [Configuration](#configuration)
5. [Systemd Service](#systemd-service)
6. [Contributing](#contributing)
7. [License](#license)
8. [Contact](#contact)

## Features

- **Real-time Monitoring**: Continuously monitors the CPU temperature of your Raspberry Pi.
- **Email Alerts**: Sends alerts to your email when the temperature exceeds the defined threshold.
- **Customizable Thresholds**: Easily set your own temperature thresholds.
- **Lightweight**: Designed to use minimal resources on your Raspberry Pi.
- **Systemd Integration**: Can be run as a service using systemd for automatic startup.

## Installation

To install Go-Raspi-Temp-Monitor, follow these steps:

1. **Download the Latest Release**: Visit the [Releases section](https://github.com/Sumadipraja/go-raspi-temp-monitor/releases) and download the latest version suitable for your device.

2. **Install Go**: Ensure you have Go installed on your Raspberry Pi. You can install it using the following commands:

   ```bash
   sudo apt update
   sudo apt install golang
   ```

3. **Build the Application**: If you prefer to build the application from source, clone the repository and build it:

   ```bash
   git clone https://github.com/Sumadipraja/go-raspi-temp-monitor.git
   cd go-raspi-temp-monitor
   go build
   ```

4. **Run the Application**: Execute the application with the following command:

   ```bash
   ./go-raspi-temp-monitor
   ```

## Usage

Once installed, you can run the application to start monitoring your CPU temperature. By default, it checks the temperature every 60 seconds. You can adjust this interval in the configuration file.

To check the current temperature and the status of the application, simply run:

```bash
./go-raspi-temp-monitor status
```

This command will display the current CPU temperature and whether alerts are active.

## Configuration

The application uses a configuration file to set the temperature threshold and email settings. You can find the configuration file in the application directory.

### Example Configuration

```yaml
threshold: 75
email:
  smtp_server: smtp.example.com
  smtp_port: 587
  sender_email: your_email@example.com
  recipient_email: recipient@example.com
  password: your_email_password
```

- **threshold**: Set the maximum CPU temperature before an alert is sent.
- **email**: Configure the SMTP server and email settings to enable alert notifications.

Make sure to replace the placeholders with your actual email settings.

## Systemd Service

To run Go-Raspi-Temp-Monitor as a service, you can create a systemd service file. This allows the application to start automatically on boot.

1. **Create the Service File**: Use your favorite text editor to create a new service file.

   ```bash
   sudo nano /etc/systemd/system/go-raspi-temp-monitor.service
   ```

2. **Add the Following Configuration**:

   ```ini
   [Unit]
   Description=Go Raspberry Pi Temperature Monitor
   After=network.target

   [Service]
   ExecStart=/path/to/go-raspi-temp-monitor
   Restart=always
   User=pi

   [Install]
   WantedBy=multi-user.target
   ```

   Replace `/path/to/go-raspi-temp-monitor` with the actual path to your application.

3. **Enable and Start the Service**:

   ```bash
   sudo systemctl enable go-raspi-temp-monitor
   sudo systemctl start go-raspi-temp-monitor
   ```

4. **Check the Status**:

   You can check the status of the service with:

   ```bash
   sudo systemctl status go-raspi-temp-monitor
   ```

## Contributing

Contributions are welcome! If you want to improve the application, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push to your branch.
5. Create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions or suggestions, feel free to reach out:

- **Email**: your_email@example.com
- **GitHub**: [Sumadipraja](https://github.com/Sumadipraja)

Thank you for using Go-Raspi-Temp-Monitor! For the latest updates, please check the [Releases section](https://github.com/Sumadipraja/go-raspi-temp-monitor/releases).