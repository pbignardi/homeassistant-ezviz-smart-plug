# EZVIZ Smart Plug Integration for Home Assistant

<p align="center">
  <img src="https://brands.home-assistant.io/ezviz/logo.png" width="200" alt="EZVIZ Logo">
</p>

[![GitHub Release][releases-shield]][releases]
[![License][license-shield]][license]
[![hacs][hacsbadge]][hacs]

A Home Assistant custom integration for EZVIZ Smart Plugs that allows you to control your EZVIZ smart plugs directly from Home Assistant.
> **Note**: This is an updated and improved version of the original project started by [@khal3d](https://github.com/khal3d/homeassistant-ezviz-smart-plug). This fork includes bug fixes, compatibility updates, and support for the latest Home Assistant versions (tested on 2025.7.x).

## Features

- Control EZVIZ smart plugs (turn on/off)
- Real-time status monitoring
- Device availability tracking
- Easy configuration through UI
- Support for multiple regions (EU, Russia)
- Automatic device discovery

## Supported Devices

- CS-T30-10A-EU
- CS-T30-10B-EU
- Any EZVIZ smart plug with device serial starting with "Q" (untested)

## Installation

### HACS (Recommended)

1. Make sure you have [HACS](https://hacs.xyz/) installed in your Home Assistant
2. In HACS, go to "Integrations"
3. Click the three dots in the top right corner and select "Custom repositories"
4. Add this repository URL: `https://github.com/maciejwaloszczyk/homeassistant-ezviz-smart-plug`
5. Select "Integration" as the category
6. Click "Add"
7. Search for "EZVIZ Smart Plug" in HACS
8. Click "Download"
9. Restart Home Assistant

### Manual Installation

1. Download the latest release from the [releases page](https://github.com/maciejwaloszczyk/homeassistant-ezviz-smart-plug/releases)
2. Extract the zip file
3. Copy the `custom_components/ezviz_plug` folder to your Home Assistant `custom_components` directory
4. Restart Home Assistant

## Configuration

### UI Configuration

1. Go to **Settings** → **Devices & Services**
2. Click **Add Integration**
3. Search for **EZVIZ Smart Plug**
4. Enter your EZVIZ account credentials:
   - **Email**: Your EZVIZ account email
   - **Password**: Your EZVIZ account password
   - **Region**: Select your region (EU or Russia)
5. Click **Submit**

The integration will automatically discover all compatible smart plugs associated with your EZVIZ account.

### YAML Configuration (Legacy/Not recommended)

```yaml
# configuration.yaml
switch:
  - platform: ezviz_plug
    email: your_email@example.com
    password: your_password
```

## Usage

Once configured, your EZVIZ smart plugs will appear as switch entities in Home Assistant. You can:

- Turn plugs on/off from the UI
- Use them in automations
- Monitor their status
- Check device availability

### Entity Attributes

Each plug entity provides the following attributes:
- `last_run_success`: Boolean indicating if the last command was successful
- `last_pressed`: Timestamp of the last state change

### Services

The integration supports standard Home Assistant switch services:
- `switch.turn_on`
- `switch.turn_off`
- `switch.toggle`

## Troubleshooting

### Common Issues

1. **Authentication Failed**
   - Verify your EZVIZ account credentials
   - Make sure your account doesn't have MFA enabled
   - Check if you selected the correct region

2. **No Devices Found**
   - Ensure your smart plugs are properly set up in the EZVIZ app
   - Verify the devices are online and connected to your account
   - Check if device serial numbers start with "Q"

3. **Connection Issues**
   - Check your internet connection
   - Verify EZVIZ cloud services are accessible
   - Try restarting the integration

### Debug Logging

To enable debug logging, add this to your `configuration.yaml`:

```yaml
logger:
  default: warning
  logs:
    custom_components.ezviz_plug: debug
    pyezviz: debug
```

## Requirements

- Home Assistant 2021.12.0 or newer (tested on 2025.7.4)
- EZVIZ account with registered smart plugs
- Internet connection for cloud API access

## Dependencies

- [pyezviz](https://github.com/BaQs/pyEzviz) - Python library for EZVIZ API

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the GPL 3.0 License - see the [LICENSE](LICENSE) file for details.

## Credits

- Original development by [@khal3d](https://github.com/khal3d)
- Uses [pyezviz](https://github.com/BaQs/pyEzviz) library for EZVIZ API communication

## Support

If you find this integration useful, please consider starring the repository!

For issues and feature requests, please use the [GitHub Issues](https://github.com/maciejwaloszczyk/homeassistant-ezviz-smart-plug/issues) page.

---

[releases-shield]: https://img.shields.io/github/release/maciejwaloszczyk/homeassistant-ezviz-smart-plug.svg?style=for-the-badge
[releases]: https://github.com/maciejwaloszczyk/homeassistant-ezviz-smart-plug/releases
[license-shield]: https://img.shields.io/github/license/maciejwaloszczyk/homeassistant-ezviz-smart-plug.svg?style=for-the-badge
[license]: https://github.com/maciejwaloszczyk/homeassistant-ezviz-smart-plug/blob/master/LICENSE
[hacs]: https://github.com/hacs/integration
[hacsbadge]: https://img.shields.io/badge/HACS-Custom-orange.svg?style=for-the-badge
