# Python 3 Setup with UV

UV is a fast Python package installer and resolver, written in Rust. It's designed to be a drop-in replacement for pip and pip-tools, with significant performance improvements.

More detailed info on the [official GitHub page](https://github.com/astral-sh/uv)

## Installation

You can install UV using pip:

```shell
pip install uv
```

Or using Homebrew on macOS:

```shell
brew install uv
```

## Basic Usage

UV can be used as a replacement for pip and pip-tools. Here are the most important features:

### How to Sync

Syncing your environment with your requirements file ensures that all packages specified in your requirements file are installed, and packages not specified are removed.

```shell
# Sync your environment with requirements.txt
uv pip sync requirements.txt

# Sync with multiple requirements files
uv pip sync requirements.txt dev-requirements.txt
```

### How to Add a Library

Adding a package to your project is straightforward:

```shell
# Install a package
uv add <package>

# Install a specific version
uv add <package>==1.2.3

# Install with extras
uv add <package>[extra]
```

### How to Add a Library to a Group

UV supports organizing dependencies into groups, which is useful for separating development dependencies from production ones:

```shell
# Create or update a requirements file for a specific group
uv add <package> --group <group-name>
```

### How to Export UV as Requirements File

You can export your current environment or compile requirements from a pyproject.toml file:

```shell
# Export current environment to requirements.txt
uv export -o requirements.txt
```

### How to Delete a Library

Removing packages is simple:

```shell
# Uninstall a package
uv remove <package>

# Uninstall multiple packages
uv remove <package> <package>
```

### How to Update

Updating packages can be done in several ways:

```shell
# Update all packages
uv update

# Update specific packages
uv update <package>
```

### How to install different python versions

```shell
# install specific python version
uv python install 3.12

# List python versions
uv python list
```

## Integration with PyCharm

1. Bottom Right corner > Add new interpreter
2. Add local intepreter
3. Type uv
4. Select your interpreter and click on the terminal icon to open a terminal
5. Use UV commands in the terminal to manage packages

## Switch from poetry to uv

1. Delete the poetry.lock
2. Delete python interpreter in pycharm
3. delete venv -> rm -rf .venv
4. Change group names from 
```toml
[tool.poetry.group.<group_name>.dependencies]
fastapi = "^0.115.1"
```
to
```toml
[dependency-groups]
<group_name> = [
    "fastapi>=0.115.1",
]
```
5. call "uv sync"

#### TIP
The easiest is to write down the names in a file and install them again with uv add --group

## Additional Resources

- [UV Documentation](https://github.com/astral-sh/uv/blob/main/README.md)
- [UV vs pip-tools Comparison](https://github.com/astral-sh/uv/blob/main/PIP-TOOLS.md)
- [UV Performance Benchmarks](https://github.com/astral-sh/uv/blob/main/BENCHMARKS.md)
