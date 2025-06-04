# Auto-blue-light-filter🌡️ 
Intelligent screen temperature adjustment for Hyprland with weather-aware automation

## ✨ Features
1. Automatic temperature adjustment based on time of day and weather
2. Location-aware using IP geolocation
3. Weather integration with OpenWeatherMap API
4. Manual and automatic modes with easy toggling
5. Blue light filter for reduced eye strain
6. Persistent state management across sessions
7. Desktop notifications for status updates
8. Comprehensive logging for troubleshooting

# 📋 Requirements

## System Requirements
1. Hyprland window manager
2. hyprsunset - Hyprland's screen temperature adjustment tool
3. Python 3.6+
4. notify-send (libnotify) for notifications

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

### Method 1: Quick Install (Recommended)
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/hypr-py-light.git
cd hypr-py-light

# Run installation script
chmod +x install.sh
./install.sh
```
### Method 2: Manual Installation
```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/hypr-py-light.git
cd hypr-py-light

# Install Python dependencies
pip3 install --user -r requirements.txt

# Make script executable
chmod +x hypr-py-light.py

# Optional: Add to PATH
cp hypr-py-light.py ~/.local/bin/hypr-py-light
```

## ⚙️ Configuration

### First Time Setup
Run the script for initial configuration:
```bash
./hypr-py-light.py
```

You'll be prompted to enter API keys for:

1. OpenWeatherMap API (for weather data)

  a. Get a free API key at: https://openweathermap.org/api
  b. Used for weather-based temperature adjustments


2. IP Geolocation API (for location detection)

  a. Get a free API key at: https://ipgeolocation.io/
  b. Used to determine your location automatically

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

# Run as background daemon
hypr-py-light
```

### Temperature Profiles
1. Day Clear: 6500K (neutral white)
2. Day Cloudy: 5800K (slightly warm)
3. Day Rainy: 5200K (warmer)
4. Night Default: 4200K (warm)
5. Night Cold: 3800K (very warm)
6. Manual Blue Light On: 5000K
7. Manual Blue Light Off: 6500K

### Systemd Service (Recommended)
1. Copy the service file:
```bash
cp hypr-py-light.service ~/.config/systemd/user/
```
2. Enable and start the service:
```bash
systemctl --user enable hypr-py-light.service
systemctl --user start hypr-py-light.service
```
3. Check service status:
```bash
systemctl --user status hypr-py-light.service
```

### Hyprland Integration
Add to your `hyprland.conf`:
```bash
# Start hypr-py-light automatically
exec-once = hypr-py-light

# Keybindings
bind = SUPER, F5, exec, hypr-py-light toggle      # Toggle blue light
bind = SUPER, F6, exec, hypr-py-light manual     # Toggle mode
bind = SUPER, F7, exec, hypr-py-light status     # Show status
```

### 📁 File Locations
1. Configuration: `~/.config/hypr-py-light/config.ini`
2. State: `~/.config/hypr-py-light/state.json`
3. Logs: `~/.config/hypr-py-light/hyprlight.log`
4. Cache: `~/.config/hypr-py-light/cache/`

## 🐛 Troubleshooting

### Common Issues
"hyprsunset command not found"
1. Install hyprsunset: `sudo pacman -S hyprsunset (Arch) or build from source`

### Temperature not changing
1. Check if hyprsunset is running: `pgrep hyprsunset`
2. Check logs: tail `~/.config/hypr-py-light/hyprlight.log`
3. Verify API keys in config file

### Location detection not working
1. Check internet connection
2. Verify IP Geolocation API key
3. Use `refresh-location` command

### Service not starting
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

1. [Hyprland] (https://hyprland.org/)- The amazing window manager
2. [hyprsunset] (https://github.com/hyprwm/hyprsunset)- Screen temperature adjustment tool
3. [OpenWeatherMap] (https://openweathermap.org/)- Weather data API
4. [IP Geolocation] (https://ipgeolocation.io/)- Location detection API

## 📊 Status Examples
`==================================================
📍 LOCATION & WEATHER
   Location: London, United Kingdom
   Weather: Clear (Clear Sky)
   Temperature: 18.5°C
   Time Period: Day

🖥️  SCREEN SETTINGS
   Screen Temperature: 6500K
   Mode: Automatic
   Blue Light Filter: OFF

📂 FILES
   Config: /home/user/.config/hypr-py-light/config.ini
   State: /home/user/.config/hypr-py-light/state.json
   Logs: /home/user/.config/hypr-py-light/hyprlight.log
=================================================`

## 🔄 Version History
1. v1.0.0 - Initial release with automatic temperature adjustment

____________________________________________________________________
Made with ❤️ for the Hyprland community
