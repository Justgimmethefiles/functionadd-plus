# functionadd+

A configuration deployment utility for Fish shell environments. `functionadd+` performs environment checks, initializes the Fish configuration path, validates configuration syntax, and installs a reusable function-management command.

## Capabilities

- Fish runtime detection and compatibility checks
- Configuration path initialization with XDG support
- Existing definition detection to prevent duplicate registration
- Pre-change configuration backup
- Syntax validation before completing deployment
- Automatic recovery when validation fails
- Deployment status and integrity reporting
- Interactive configuration editing through Nano

## Requirements

- Linux
- Python 3.10 or newer
- Fish shell
- Nano

No third-party Python packages are required.

## Installation

Clone the repository and enter the project directory:

```sh
git clone https://github.com/YOUR-USERNAME/functionadd-plus.git
cd functionadd-plus
```

Run the deployment utility:

```sh
python3 functionadd_plus.py
```

The utility checks the environment, prepares the configuration directory, backs up an existing configuration when necessary, registers the `functionadd+` command, and validates the resulting Fish configuration. If validation fails, it attempts to restore the prior configuration.

## Activation

After successful deployment, load the updated configuration into the current Fish session:

```fish
source ~/.config/fish/config.fish
```

If your Fish configuration uses a custom `XDG_CONFIG_HOME`, source the `config.fish` file under that directory instead.

Run the installed command:

```fish
functionadd+
```

This opens the Fish configuration in Nano. Add new function definitions at the bottom of the file. Save with **Ctrl+O**, confirm with **Enter**, and exit with **Ctrl+X**. The command sources the configuration after Nano exits successfully.

## Configuration and recovery

The default configuration path is `~/.config/fish/config.fish`. When `XDG_CONFIG_HOME` is set, the utility uses `$XDG_CONFIG_HOME/fish/config.fish`.

Before modifying an existing configuration, the utility creates a backup named `config.fish.functionadd-plus.bak`. Syntax validation uses Fish's no-execution mode, so the configuration is checked without running its commands. If validation fails, the utility attempts to restore the previous file.

If the command is already registered, the utility leaves the configuration unchanged.

## Troubleshooting

**Fish shell was not found**

Install Fish with your distribution's package manager and rerun the utility.

**Configuration validation fails**

Review the syntax error reported by Fish. The utility attempts to restore the previous configuration if validation does not pass.

**The command is unavailable in the current session**

Source your Fish configuration, then run `functionadd+` again.

## License and copyright

Copyright (c) 2026. All rights reserved. No license is granted to copy, modify, redistribute, or republish this software without prior written permission, except where permitted by applicable law.
