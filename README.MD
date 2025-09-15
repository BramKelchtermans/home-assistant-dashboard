# Home Assistant UI Lovelace Minimalist Dashboard

This repository contains a complete Home Assistant dashboard configuration and custom cards designed for the [UI Lovelace Minimalist (ULM)](https://ui-lovelace-minimalist.github.io/UI/setup/download/) theme.

## 📋 Prerequisites

Before using this dashboard, ensure you have:

1. **Home Assistant** running (preferably with HACS installed)
2. **UI Lovelace Minimalist theme** installed via HACS or manually
3. **Required integrations and resources** as specified in the [ULM documentation](https://ui-lovelace-minimalist.github.io/UI/setup/download/)

### Required Integrations

- `browser_mod` by Thomas Lovén (for popup functionality)

### Required Lovelace Resources

- `button-card` by RomRider
- `card-mod` by Thomas Lovén
- `mini-graph-card` by Karl Kihlström
- `Mini Media Player` by Karl Kihlström
- `My Cards Bundle` by AnthonMS
- `Light Entity Card` by Leonardo Merza
- `auto-entities` by Thomas Lovén
- `simple-weather-card` by Karl Kihlström
- `weather-radar-card` by Makin-Things
- `lovelace-layout-card` by Thomas Lovén
- `lovelace-state-swtch` by Thomas Lovén

## 🚀 Installation

### Step 1: Install UI Lovelace Minimalist Theme

Follow the official installation guide at [UI Lovelace Minimalist Setup](https://ui-lovelace-minimalist.github.io/UI/setup/download/).

### Step 2: Copy Dashboard Files

1. Copy the `dashboard/` folder to your Home Assistant's `ui_lovelace_minimalist/` directory:

   ```
   /config/custom_components/ui_lovelace_minimalist/dashboard/
   ```

2. Copy the `custom_cards/` folder to your Home Assistant's `ui_lovelace_minimalist/` directory:
   ```
   /config/custom_components/ui_lovelace_minimalist/custom_cards/
   ```

### Step 3: Configure Lovelace

1. In Home Assistant, go to **Configuration** → **Lovelace Dashboards**
2. Create a new dashboard or edit an existing one
3. Set the dashboard configuration to use the `ui-lovelace.yaml` file
4. Restart Home Assistant

## 📁 Repository Structure

### Dashboard Views

The dashboard is organized into multiple views:

- **🏠 Home** - Welcome screen with weather and person tracking
- **🏡 House** - General house information and vacuum control
- **��️ Living** - Living room climate, TV, and lighting controls
- **�� Kitchen** - Kitchen devices, temperature, and sensors
- **��️ Bedroom** - Bedroom TV, lighting, and air conditioning
- **�� Lab** - Computer monitoring, 3D printer, and network status
- **💼 Workplace** - Work area switches and equipment
- **📦 Storage** - Storage area and laundry room controls
- **⚡ Energy** - Energy consumption graphs and pricing
- **🖥️ Proxmox** - Virtual machine and server monitoring
- **🚗 Car** - Vehicle information and door status

### Custom Cards

This repository includes several custom button-card templates:

#### Core Cards

- **`custom_card_bram_entities`** - Multi-entity display with customizable icons and states
- **`custom_card_bram_room`** - Room overview with temperature, lighting, and sensor status
- **`custom_card_bram_thermostat`** - Thermostat control with temperature display
- **`custom_card_button_bram`** - Customizable button with state management
- **`custom_card_computer`** - Computer monitoring with system stats

#### Chips

- **`custom_chip_icon_bram`** - Icon-only chip with custom SVG support

## 🎨 Customization

### Entity Configuration

Most cards use variables for easy customization. Key variables include:

- `ulm_card_vertical_button_color` - Button color theme
- `ulm_card_vertical_button_state` - Active state value
- `ulm_language` - Language setting (default: "nl")
- `background_url` - Custom background images for room cards

### Adding New Entities

To add new entities to existing cards:

1. Edit the relevant YAML file in the dashboard folder
2. Add your entity configuration following the existing patterns
3. Update any required variables in the custom card templates

### Creating New Views

1. Create a new folder in the `dashboard/` directory
2. Add your view configuration to `ui-lovelace.yaml`
3. Create YAML files for your cards using `!include_dir_list`

## 🔧 Configuration Examples

### Room Card with Temperature

```yaml
- type: "custom:button-card"
  template: "card_bram_room"
  entity: light.living_room
  variables:
    climate_id: climate.living_room
    temperature_sensor: sensor.living_room_temperature
    show_pct: true
    sensor1_id: binary_sensor.living_room_motion
    icon1_on: "mdi:motion-sensor"
    icon1_off: "mdi:motion-sensor-off"
```

### Multi-Entity Card

```yaml
- type: "custom:button-card"
  template: "card_bram_entities"
  entity: input_boolean.example
  variables:
    ulm_card_vertical_button_color: "blue"
    ulm_card_vertical_button_state: "on"
    entity_1:
      entity: sensor.temperature
      icon: "mdi:thermometer"
      color: "255,0,0"
      unit: "°C"
```

## 🌐 Language Support

The dashboard is configured for Dutch (nl) by default. To change the language:

1. Update the `ulm_language` variable in your cards
2. Modify the translation strings in the custom card templates
3. Update the welcome card greetings and labels

## 📱 Mobile Optimization

The dashboard includes mobile-optimized settings:

- Kiosk mode configuration
- Responsive card layouts
- Touch-friendly button sizes

## 🤝 Contributing

Feel free to submit issues and enhancement requests! This dashboard is designed to be easily customizable and extensible.

## License

This project is open source and available under the same license as the UI Lovelace Minimalist theme.

## Links

- [UI Lovelace Minimalist Documentation](https://ui-lovelace-minimalist.github.io/UI/)
- [Home Assistant](https://www.home-assistant.io/)
- [HACS (Home Assistant Community Store)](https://hacs.xyz/)

---

**Note**: This dashboard is designed for a specific Home Assistant setup. You may need to adjust entity names, integrations, and configurations to match your specific setup.
