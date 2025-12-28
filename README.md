# Home Assistant Blueprints

A collection of Home Assistant automation blueprints for smart home control.

## Blueprints

### 🌡️ Window/Door Heating Control

Automatically controls heating based on window and door states. When windows or doors are left open, the heating temperature is lowered to save energy. When all windows and doors are closed, heating is restored to the normal schedule.

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fn-atanasov%2Fhome-assistant%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Fwindow_door_heating_control.yaml)

#### Features

- ✅ **No external helpers required** - Works without pre-created input_boolean or input_number entities
- ✅ **Configurable delay** - Wait before lowering temperature to avoid false triggers from quick open/close
- ✅ **Multiple sensors** - Support for multiple window/door sensors per zone
- ✅ **Mobile notifications** - Optional notifications to multiple mobile devices
- ✅ **Zone-based** - Create separate automations for different rooms/zones
- ✅ **Idempotent** - Safe to trigger multiple times without side effects

#### How It Works

1. **Window/Door Opens**: 
   - Waits for the configured delay (default: 60 seconds)
   - Verifies window/door is still open
   - Lowers heating to the configured temperature (default: 10°C)
   - Sends optional mobile notification

2. **All Windows/Doors Close**:
   - Restores heating to "schedule" preset mode
   - Sends optional mobile notification

#### Inputs

| Input | Description | Default |
|-------|-------------|---------|
| Window/Door Sensors | Binary sensors detecting open windows/doors | Required |
| Climate Entity | The thermostat/climate entity to control | Required |
| Open Window Temperature | Temperature when windows are open | 10°C |
| Delay | Seconds to wait before lowering temperature | 60s |
| Devices to Notify | Mobile devices for notifications | None |
| Zone Name | Name for notifications and logging | Required |

#### Requirements

- Home Assistant 2024.1.0 or newer
- Climate integration with `set_temperature` and `set_preset_mode` services
- Binary sensors for windows/doors
- (Optional) Mobile app for notifications

#### Installation

1. Click the "Import Blueprint" button above, or:
2. Go to **Settings** → **Automations & Scenes** → **Blueprints**
3. Click **Import Blueprint**
4. Paste this URL:
   ```
   https://github.com/n-atanasov/home-assistant/blob/main/blueprints/automation/window_door_heating_control.yaml
   ```

#### Usage

After importing, create a new automation from the blueprint:

1. Go to **Settings** → **Automations & Scenes** → **Create Automation**
2. Select **"Window/Door Heating Control"** blueprint
3. Configure the inputs for your zone
4. Save and enable the automation

Create one automation per zone/room for granular control.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Author

Created by [@n-atanasov](https://github.com/n-atanasov)

