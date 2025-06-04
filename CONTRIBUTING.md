# Contributing to Auto-blue-light-filter 

Thank you for your interest in contributing! This document provides guidelines for contributing to the project.

## How to Contribute

### Reporting Bugs
- Use the GitHub issue tracker
- Include system information (OS, Python version, Hyprland version)
- Provide steps to reproduce the issue
- Include relevant log files

### Suggesting Features
- Open an issue with the "enhancement" label
- Describe the feature and its use case
- Explain why it would be valuable

### Code Contributions
1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Test thoroughly
5. Commit with clear messages
6. Push and create a pull request

### Code Style
- Follow PEP 8 for Python code
- Use meaningful variable names
- Add comments for complex logic
- Include docstrings for functions

### Testing
- Test on multiple systems if possible
- Verify all commands work correctly
- Check that the daemon runs without issues

## Development Setup

```bash
# Clone your fork
git clone https://github.com/IamAndelib/Auto-blue-light-filter.git
cd Auto-blue-light-filter

# Install in development mode
pip3 install -e .

# Make changes and test
./hypr-py-light.py status
