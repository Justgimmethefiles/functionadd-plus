# functionadd+

**A comically overengineered installer for a tiny Fish shell function.**

`functionadd+` displays a dramatic terminal deployment sequence full of progress bars, scientific-looking telemetry, hexadecimal IDs, and deeply unnecessary subsystem names. Once the theatrics finish, it adds this small function to your Fish configuration:

```fish
function functionadd+
    nano ~/.config/fish/config.fish
    source ~/.config/fish/config.fish
end
```

The technical-looking telemetry is **simulated for comedy**. The app does not tune the kernel, benchmark hardware, perform quantum computing, or optimize Fish itself.

## Requirements

- Linux
- Python 3.10 or newer
- Fish shell

No third-party Python packages are required.

## Run it

Clone the repository, enter the directory, and run:

```sh
python3 functionadd_plus.py
```

The script:
- checks whether Fish is installed;
- creates `~/.config/fish` if needed;
- avoids adding a duplicate function;
- creates a backup of an existing `config.fish` before editing it;
- validates the resulting config with `fish --no-execute`;
- attempts to restore the backup if validation fails.

It does **not** execute the Fish config as part of validation. After success, reload the config in your current Fish session:

```fish
source ~/.config/fish/config.fish
```

Then run:

```fish
functionadd+
```

When `functionadd+` opens `config.fish` in Nano, add your new function at the very bottom of the file. Press **Ctrl+O**, then **Enter**, then **Ctrl+X**. The function will be saved, and the config will be sourced automatically by the function.

## Safety notes

Read scripts before running them, especially scripts that edit shell configuration. This project writes only to the Fish config path shown in its output. If the function already exists, the script leaves the file unchanged.

The default function opens `~/.config/fish/config.fish` in `nano` and sources that file when you exit. If you use a different editor, change `nano` in the function body.

## GitHub

Create an empty GitHub repository named `functionadd-plus`, then push this directory:

```sh
git init
git add README.md LICENSE .gitignore functionadd_plus.py
git commit -m "Add functionadd+ comedy installer"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/functionadd-plus.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your GitHub username.

## License

MIT. See [LICENSE](LICENSE).
