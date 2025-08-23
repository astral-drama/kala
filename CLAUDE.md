# Kala Time Server Development Notes

## Project Goal
Build a Debian package that configures a Raspberry Pi as an NTP time server using chrony.

## Package Structure
- **Package name**: kala-timeserver
- **Main dependency**: chrony
- **Target platform**: Raspberry Pi / Debian-based systems

## Key Tasks
1. Create debian/ directory structure
2. Configure chrony for time server mode
3. Set up postinst script for service configuration
4. Define package dependencies and metadata

## Chrony Configuration
- Enable NTP server for local network (allow directive)
- Configure reliable upstream NTP sources
- Set appropriate stratum level
- Enable RTC synchronization if available

## Build Commands
```bash
dpkg-buildpackage -us -uc -b  # Build binary package
dpkg -i kala-timeserver_*.deb  # Install package
```