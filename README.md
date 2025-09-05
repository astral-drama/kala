# Kala Time Server

A Debian package for configuring Raspberry Pi as a precision network time server using chrony with GPS/PPS support.

## Overview

This package automates the setup and configuration of a Raspberry Pi as a high-precision NTP time server for your local network using chrony. It supports both standard NTP operation and precision timing with GPS and PPS (Pulse Per Second) sources.

## Features

- Configures chrony for optimal time server operation with GPS/PPS support
- Auto-detects GPS hardware and configures appropriately  
- Supports Raspberry Pi Ultimate GPS HAT with automatic PPS configuration
- Enables NTP server for local network clients
- Automatic serial port and UART configuration for GPS
- Fallback to standard NTP sources when GPS unavailable
- Comprehensive monitoring and diagnostic commands
- Automatic service configuration and startup

## Requirements

- Raspberry Pi running Debian/Raspberry Pi OS
- Network connectivity
- Internet access for initial time synchronization
- Optional: Raspberry Pi Ultimate GPS HAT for precision timing

## Installation

```bash
# Use apt to automatically resolve and install dependencies
sudo apt install ./kala-timeserver_*.deb

# Alternative: If chrony is already installed
sudo dpkg -i kala-timeserver_*.deb
```

## Dependencies

- chrony (NTP daemon)
- gpsd, gpsd-clients (GPS daemon and tools)
- pps-tools (PPS testing utilities)  
- python3-gps (GPS Python utilities)

## Configuration

The package automatically configures the system based on detected hardware:

### With GPS Hardware
When GPS hardware is detected (e.g., Raspberry Pi Ultimate GPS HAT):
- Installs GPS-enhanced chrony configuration with PPS support
- Configures gpsd for /dev/ttyAMA0 communication
- Enables PPS support via GPIO4
- Provides nanosecond-precision timing
- Automatic serial port configuration

### Standard Configuration  
Without GPS hardware:
- Installs standard chrony configuration
- Uses public NTP pool servers
- Suitable for general network time serving

After installation, the time server will be available on your local network. Clients can use this server's IP address as their NTP server.

## Monitoring Commands

### GPS Status
```bash
gpsmon          # Real-time GPS data monitor
cgps -s         # GPS info display
ppstest /dev/pps0  # Test PPS signal
```

### Chrony Status
```bash
chronyc sources     # View time sources
chronyc sourcestats # GPS/PPS statistics  
chronyc serverstats # Server statistics
```

## Building from Source

```bash
dpkg-buildpackage -us -uc -b
```

## License

MIT