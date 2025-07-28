# Contributing to Temperature Monitor

Thank you for your interest in contributing to Temperature Monitor! 🌡️ We welcome contributions from the community and are pleased to have you aboard.

## 🤝 How to Contribute

There are many ways to contribute to this project:

- 🐛 **Report bugs** - Help us identify issues
- ✨ **Suggest features** - Share your ideas for improvements  
- 📖 **Improve documentation** - Make it clearer and more comprehensive
- 🔧 **Submit code** - Fix bugs or implement new features
- 🧪 **Test on different systems** - Help ensure compatibility
- 🌍 **Translate** - Add support for more languages

## 🚀 Getting Started

### Development Setup

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/yourusername/temperature-monitor.git
   cd temperature-monitor
   ```
3. **Make scripts executable**:
   ```bash
   chmod +x temp-monitor install desktop-integration
   ```
4. **Test basic functionality**:
   ```bash
   ./temp-monitor --test
   ```

### System Requirements for Development

- **Linux system** (any major distribution)
- **lm-sensors** installed and configured
- **bash** 4.0 or later
- **Git** for version control
- **Text editor** of your choice

Optional but recommended:
- **shellcheck** for script linting
- **Different terminal emulators** for testing (urxvt, alacritty, xterm, etc.)
- **Multiple desktop environments** for integration testing

## 🔧 Development Workflow

### 1. Create a Branch

Create a feature branch for your work:
```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/issue-description
```

### 2. Make Your Changes

- Keep changes **focused and atomic** - one feature/fix per PR
- Follow the **existing code style** (see Style Guide below)  
- **Test thoroughly** on your system
- **Update documentation** if needed

### 3. Test Your Changes

Before submitting, make sure to test:

```bash
# Basic functionality
./temp-monitor --test
./temp-monitor --help
./temp-monitor --config

# Installation process
./install --help  # Should not crash

# Desktop integration
./desktop-integration  # If you have a GUI environment

# Script syntax (if shellcheck is available)
shellcheck temp-monitor install desktop-integration
```

### 4. Commit Your Changes

Write clear, descriptive commit messages:

```bash
git add .
git commit -m "Add support for AMD temperature sensors

- Detect k10temp module for AMD CPUs
- Add fallback for systems without coretemp
- Update documentation with AMD-specific troubleshooting

Fixes #123"
```

### 5. Push and Create PR

```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub using the provided template.

## 📋 Style Guide

### Shell Script Style

- **Use 4 spaces** for indentation (no tabs)
- **Quote variables** to prevent word splitting: `"$variable"`
- **Use descriptive variable names**: `temp_value` not `tv`
- **Add comments** for complex logic
- **Use consistent function naming**: `snake_case`
- **Prefer `[[ ]]` over `[ ]`** for conditionals
- **Use `local` for function variables**

#### Example:
```bash
# Good
get_temperature_color() {
    local temp_value="$1"
    local temp_int=$(echo "$temp_value" | sed 's/[^0-9]//g')
    
    if [[ "$temp_int" -gt "$TEMP_CRITICAL" ]]; then
        echo "${COLOR_CRITICAL}🔴${COLOR_RESET}"
    fi
}

# Avoid
getTempColor() {
    t=$1
    if [ $t -gt 90 ]; then
        echo "red"
    fi
}
```

### Documentation Style

- **Use clear, concise language**
- **Include examples** when helpful
- **Keep README up to date** with new features
- **Use emojis sparingly** but consistently
- **Test all commands** mentioned in documentation

### Commit Message Style

Follow the conventional commits format:
```
type(scope): brief description

Longer explanation if needed

- Bullet points for details
- Reference issues: Fixes #123
- Breaking changes: BREAKING CHANGE: details
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

## 🧪 Testing Guidelines

### Manual Testing Checklist

Before submitting a PR, test on:

- [ ] **Basic functionality**: `temp-monitor --test` works
- [ ] **Help commands**: `--help`, `--info`, `--config` work
- [ ] **Configuration**: `--edit-config` opens editor
- [ ] **Installation**: `./install` completes without errors
- [ ] **Desktop integration**: App appears in menu (if GUI available)
- [ ] **Different terminals**: Works with xterm, gnome-terminal, etc.
- [ ] **Error handling**: Graceful failures with helpful messages

### Testing on Different Systems

We especially welcome testing on:
- **Different distributions**: Debian, Ubuntu, Fedora, Arch, openSUSE
- **Different desktop environments**: GNOME, KDE, XFCE, MATE
- **Different hardware**: Intel vs AMD CPUs, laptops vs desktops
- **Edge cases**: Systems without sensors, minimal installations

### Automated Testing

The project includes GitHub Actions CI that automatically:
- Lints shell scripts with shellcheck
- Tests basic functionality on Ubuntu
- Validates script syntax
- Tests installation process

## 🐛 Bug Reports

When reporting bugs, please include:

- **Operating system** and version
- **Desktop environment** (if applicable)
- **Output of `sensors`** command
- **Output of `temp-monitor --debug`** (if available)
- **Steps to reproduce** the issue
- **Expected vs actual behavior**
- **Error messages** (full text, not screenshots)

Use the provided bug report template when creating issues.

## ✨ Feature Requests

For feature requests, please:

- **Check existing issues** first to avoid duplicates
- **Describe the problem** your feature would solve
- **Explain your proposed solution** in detail
- **Consider alternative approaches**
- **Think about compatibility** with different systems

Use the provided feature request template.

## 🌍 Internationalization

We welcome translations and localization improvements:

- **Desktop files**: Translate Name and Comment fields
- **Help text**: Add translated versions of help messages
- **Error messages**: Translate user-facing error messages
- **Documentation**: Translate README sections

## 📖 Documentation Contributions

Documentation improvements are always welcome:

- **Fix typos** and grammar errors
- **Clarify instructions** that are confusing
- **Add missing information** 
- **Update outdated content**
- **Improve formatting** and readability
- **Add screenshots** or examples

## 🚫 What We Don't Accept

Please avoid:

- **Breaking changes** without discussion
- **Platform-specific code** that breaks compatibility
- **Unnecessary dependencies** 
- **Code that requires root privileges** unnecessarily
- **Features that significantly increase complexity**
- **Changes without testing**
- **Commits that mix multiple unrelated changes**

## 📞 Getting Help

If you need help with contributing:

- 💬 **GitHub Discussions**: Ask questions and discuss ideas
- 🐛 **Issues**: Report bugs or request features  
- 📧 **Email**: Contact maintainers directly (see README)

## 🎉 Recognition

Contributors are recognized in:
- **GitHub contributors** page
- **Release notes** for significant contributions
- **README acknowledgments** for major features

## 📄 License

By contributing to Temperature Monitor, you agree that your contributions will be licensed under the same MIT License that covers the project.

## 🙏 Thank You!

Every contribution, no matter how small, makes Temperature Monitor better for everyone in the Linux community. Thank you for taking the time to contribute! 🌟

---

**Happy coding!** 🚀 If you have any questions about contributing, don't hesitate to ask.