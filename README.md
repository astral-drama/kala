# Kala Time Server

A Debian package for configuring Raspberry Pi as a network time server using chrony.

## Overview

This package automates the setup and configuration of a Raspberry Pi as a reliable NTP time server for your local network using chrony.

## Features

- Configures chrony for optimal time server operation
- Enables NTP server for local network clients
- Automatic service configuration and startup
- Suitable for Raspberry Pi deployment

## Requirements

- Raspberry Pi running Debian/Raspberry Pi OS
- Network connectivity
- Internet access for initial time synchronization

## Installation

```bash
sudo dpkg -i kala-timeserver_*.deb
```

## Dependencies

- chrony

## Configuration

After installation, the time server will be available on your local network. Clients can use this server's IP address as their NTP server.

## Building from Source

```bash
dpkg-buildpackage -us -uc -b
```

## License

MIT