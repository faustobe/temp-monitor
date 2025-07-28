# 🌡️ Temperature Monitor

A lightweight, real-time CPU temperature monitor for Linux with transparent terminal interface and process tracking.

![Temperature Monitor Screenshot](https://img.shields.io/badge/platform-Linux-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Shell](https://img.shields.io/badge/shell-bash-yellow.svg)

## ✨ Features

- 🌡️ **Real-time temperature monitoring** for all CPU cores and sensors
- 📊 **Top CPU processes tracker** - see what's heating up your system
- 🎨 **Color-coded temperature indicators** (🟢 Normal, 🟡 Warm, 🟠 Hot, 🔴 Critical)
- 🪟 **Transparent terminal window** - stays out of the way
- ⚙️ **Customizable temperature thresholds** - set your own limits
- 🔔 **Desktop notifications** for high temperatures
- 🎯 **Multi-terminal support** (urxvt, alacritty, xterm, gnome-terminal, etc.)
- 🌍 **Universal desktop integration** (GNOME, KDE, XFCE, MATE, etc.)
- 🛠️ **Easy installation** with automatic dependency handling

## 🖼️ Screenshots

```
🌡️ Termometro CPU
──────────────────────────
Core 0:         +57.0°C 🟢
Core 1:         +57.0°C 🟢
CPU Package:    +57.0°C 🟢
WiFi temp:      +56.0°C 🟢
Chipset temp:   +27.8°C 🟢
──────────────────────────
Top CPU:
brave          26.3%
codium         12.5%
xfce4-session   7.5%
──────────────────────────
Ctrl+C per uscire
```

## 🚀 Quick Start

### One-line Installation
```bash
curl -fsSL https://raw.githubusercontent.com/yourusername/temperature-monitor/main/install | bash
```

### Manual Installation
```bash
git clone https://github.com/yourusername/temperature-monitor.git
cd temperature-monitor
chmod +x install
./install
```

### First Run
```bash
temp-monitor
```

That's it! The monitor will open in a transparent window.

## 📋 Usage

### Basic Commands
```bash
temp-monitor                    # Open transparent monitor window
temp-monitor --test            # Show current temperatures once
temp-monitor --config          # Show current configuration
temp-monitor --edit-config     # Edit temperature thresholds
temp-monitor --info            # Show detailed information
temp-monitor --help            # Show all options
```

### Quick Shortcuts
```bash
temp                           # Alias for temp-monitor
temperatures                   # Quick temperature check
temp-test                      # Same as --test
```

### Desktop Integration
After installation, find **Temperature Monitor** in:
- **GNOME**: Activities → Show Applications
- **KDE/Plasma**: Application Menu → System
- **XFCE**: Applications Menu → System  
- **MATE**: Applications → System Tools
- **Others**: Look in System/Administration category

## ⚙️ Configuration

### Temperature Thresholds
Edit `~/.config/termometro-cpu/config`:

```bash
# Temperature thresholds (°C)
TEMP_NORMAL=60      # 🟢 Green: Normal temperatures
TEMP_WARNING=75     # 🟡 Yellow: Getting warm
TEMP_HIGH=85        # 🟠 Orange: Hot
TEMP_CRITICAL=90    # 🔴 Red: Critical - take action!

# Notifications
ENABLE_NOTIFICATIONS=true
NOTIFY_WARNING=true
NOTIFY_CRITICAL=true
NOTIFY_COOLDOWN=300     # Seconds between notifications

# Update interval
UPDATE_INTERVAL=2       # Seconds
```

### Quick Configuration
```bash
temp-monitor --edit-config    # Opens editor
temp-monitor --config         # Shows current settings
```

## 🔧 Troubleshooting

### Sensors Not Working
```bash
# Install and detect sensors
sudo sensors-detect --auto

# For Intel CPUs
sudo modprobe coretemp

# For AMD CPUs  
sudo modprobe k10temp

# Test sensors
sensors
```

### After Suspend/Resume Issues
```bash
# Reset sensor modules (common after long suspend)
sudo modprobe -r coretemp && sudo modprobe coretemp

# Or use the built-in fix
temp-monitor --fix-sensors
```

### No Terminal Found
The installer automatically detects and installs compatible terminals. Supported:
- **Best transparency**: urxvt, alacritty
- **Good compatibility**: xfce4-terminal, gnome-terminal, konsole
- **Basic fallback**: xterm

### Permission Issues
```bash
# Never run as root
whoami  # Should NOT be root

# Fix permissions if needed
chmod +x ~/.local/bin/temp-monitor
```

## 🏗️ Requirements

### System Requirements
- **OS**: Linux (any distribution)
- **Architecture**: x86_64, ARM64
- **Display**: X11 or Wayland
- **Memory**: < 10MB RAM usage

### Dependencies
Auto-installed by the installer:
- `lm-sensors` - Hardware sensor access
- `bc` - Mathematical calculations  
- Compatible terminal emulator
- `notify-send` (optional) - Desktop notifications

### Supported Distributions
- ✅ **Debian/Ubuntu** and derivatives
- ✅ **Fedora/CentOS/RHEL**
- ✅ **Arch Linux/Manjaro**
- ✅ **openSUSE**
- ✅ **Most other distributions** with package manager auto-detection

## 🏠 File Structure

After installation:
```
~/.local/bin/temp-monitor                    # Main executable
~/.config/termometro-cpu/config              # Configuration file
~/.local/share/applications/temperature-monitor.desktop  # Desktop integration
~/.local/share/icons/hicolor/*/apps/temperature-monitor.*  # Icons
```

## 🧪 Advanced Usage

### Custom Temperature Ranges
```bash
# Conservative settings (servers)
TEMP_NORMAL=50
TEMP_WARNING=65
TEMP_HIGH=75
TEMP_CRITICAL=80

# Relaxed settings (gaming rigs)
TEMP_NORMAL=70
TEMP_WARNING=80
TEMP_HIGH=90
TEMP_CRITICAL=95
```

### Integration with System Monitoring
```bash
# Add to startup applications
temp-monitor --daemon &

# Use in scripts
TEMP=$(temp-monitor --get-max-temp)
if [ "$TEMP" -gt 80 ]; then
    echo "System too hot: ${TEMP}°C"
fi
```

### Keyboard Shortcuts
Add to your desktop environment:
- **Command**: `temp-monitor`
- **Suggested shortcut**: `Ctrl+Alt+T`
- **Or**: `Super+T`

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Development Setup
```bash
git clone https://github.com/yourusername/temperature-monitor.git
cd temperature-monitor
./temp-monitor --test  # Test your changes
```

### Reporting Issues
Please include:
- Distribution and version
- Desktop environment
- Output of `sensors`
- Output of `temp-monitor --debug`

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **lm-sensors project** for hardware sensor access
- **Linux community** for testing and feedback
- **Terminal developers** for transparency support

## 📞 Support

- 🐛 **Issues**: [GitHub Issues](https://github.com/yourusername/temperature-monitor/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/yourusername/temperature-monitor/discussions)
- 📧 **Email**: your.email@example.com

---

<div align="center">

**⭐ Star this repository if you find it useful! ⭐**

Made with ❤️ for the Linux community

</div>
