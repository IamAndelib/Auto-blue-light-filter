# Auto-blue-light-filter🌡️ 
Automatic screen temperature adjustment tool for Hyprland, intelligently adjusting your display's colour temperature based on the time of day, weather conditions, and location.

## ✨ Features
- **Automatic temperature adjustment** based on time of day and weather
- **Location-aware** using IP geolocation
- **Weather integration** with OpenWeatherMap API
- **Manual and automatic modes** with easy toggling
- **Blue light filter** for reduced eye strain
- **Desktop notifications** for status updates
- **Comprehensive logging** for troubleshooting

# 📋 Requirements

## System Requirements
- **Hyprland** window manager
- **hyprsunset** - Hyprland's screen temperature adjustment tool
- **Python 3.6+**
- **notify-send** (libnotify) for notifications

## Installation of Dependencies

### Arch:
```bash
sudo pacman -S hyprsunset python python-requests
```
### Ubuntu/Debian:
```bash
# Install hyprsunset from source (see hyprsunset documentation)
sudo apt install python3 python3-pip python3-requests libnotify-bin
```

## 🚀 Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/hypr-py-light.git
cd hypr-py-light
chmod +x hypr-py-light.py
```

## ⚙️ Configuration

### First Time Setup
Run the script for initial configuration:
```bash
./hypr-py-light.py
```

You'll be prompted to enter API keys for:

1. **OpenWeatherMap API** (for weather data)
  - Get a free API key at: https://openweathermap.org/api
  - Used for weather-based temperature adjustments

2. **IP Geolocation API** (for location detection)
  - Get a free API key at: https://ipgeolocation.io/
  - Used to determine your location automatically

### Manual Configuration
Edit `~/.config/hypr-py-light/config.ini`:
```ini
[API]
openweather = your_openweather_api_key_here
ipgeolocation = your_ipgeolocation_api_key_here
```

## 🎛️ Usage

### Basic Commands
```bash
# Show current status
hypr-py-light status

# Toggle between manual and automatic modes
hypr-py-light manual

# Force automatic mode
hypr-py-light auto

# Force manual mode
hypr-py-light force-manual

# Toggle blue light filter (manual mode only)
hypr-py-light toggle

# Refresh location data
hypr-py-light refresh-location

# Test with specific temperature
hypr-py-light test 4500

# Run as a background daemon
hypr-py-light
```

### Temperature Profiles
1. **Day Clear:** 6500K (neutral white)
2. **Day Cloudy:** 5800K (slightly warm)
3. **Day Rainy:** 5200K (warm)
4. **Night Default:** 4600K (warmer)
5. **Night Cold:** 4200K (very warm)
6. **Manual Blue Light On:** 5000K
7. **Manual Blue Light Off:** 6500K

### Hyprland Integration
Add to your `hyprland.conf`:
```bash
# Start hypr-py-light automatically
exec-once = /path-to-blue-light.py

# Keybindings
bind = SUPER, F5, exec, ~/path-to-hypr-py-light toggle     # Toggle blue light in manual mode
bind = SUPER, F6, exec, ~/path-to-hypr-py-light manual     # Toggle mode (auto/manual)
bind = SUPER, F7, exec, ~/path-to-hypr-py-light status     # Show status
```

### 📁 File Locations
1. **Configuration:** `~/.config/hypr-py-light/config.ini`
2. **State:** `~/.config/hypr-py-light/state.json`
3. **Logs:** `~/.config/hypr-py-light/hyprlight.log`
4. **Cache:** `~/.config/hypr-py-light/cache/`

## 🐛 Troubleshooting

### Common Issues
**"hyprsunset command not found"**
1. Install hyprsunset: `sudo pacman -S hyprsunset (Arch) or build from source`

**Temperature not changing**
1. Check if hyprsunset is running: `pgrep hyprsunset`
2. Check logs: tail `~/.config/hypr-py-light/hyprlight.log`
3. Verify API keys in config file

**Location detection not working**
1. Check internet connection
2. Verify IP Geolocation API key
3. Use `refresh-location` command

**Service not starting**
1. Check systemd logs: `journalctl --user -u hypr-py-light.service`
2. Ensure script has execute permissions
3. Verify Python dependencies are installed

## Debug Mode
Check detailed logs:
```bash
tail -f ~/.config/hypr-py-light/hyprlight.log
```

## 🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss the changes you would like to make.

1. Fork the repository
2. Create your feature branch `(git checkout -b feature/AmazingFeature)`
3. Commit your changes `(git commit -m 'Add some AmazingFeature')`
4. Push to the branch `(git push origin feature/AmazingFeature)`
5. Open a Pull Request

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

1. [Hyprland](https://hyprland.org/) - The amazing window manager
2. [hyprsunset](https://github.com/hyprwm/hyprsunset) - Screen temperature adjustment tool
3. [OpenWeatherMap](https://openweathermap.org/) - Weather data API
4. [IP Geolocation](https://ipgeolocation.io/) - Location detection API

## 📊 Status Examples
```
=========================================================
📍 LOCATION & WEATHER
   Location: London, United Kingdom
   Weather: Clear (Clear Sky)
   Temperature: 18.5°C
   Time: Day

🖥️ SCREEN SETTINGS
   Screen Temperature: 6500K
   Mode: Automatic
   Blue Light Filter: OFF

📂 FILES
   Config: /home/user/.config/hypr-py-light/config.ini
   State: /home/user/.config/hypr-py-light/state.json
   Logs: /home/user/.config/hypr-py-light/hyprlight.log
==========================================================
```

## 🔄 Version History
1. **v1.0.0** - Initial release with automatic temperature adjustment

____________________________________________________________________
Made with ❤️ for the Hyprland community
