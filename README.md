# Python Project Template

A modern Python project template using `uv` for dependency management.

## How to Download the Files

If you have a github account you can use this repository as a template to
create your own project. If you do not have a github account, you can
download the files directly as follows:

1. Click the green "Code" button at the top of the repository
2. Select "Download ZIP"
3. Extract the ZIP file to your desired location
4. Open Terminal and navigate to the extracted folder:
   ```bash
   cd path/to/extracted-folder
   ```

## Initializing the Project

1. **Install uv**

   `uv` is a tool to streamline the setup and management of Python projects.
   The following command installs `uv` if it is not already installed on your system.

   ```sh
   command -v uv >/dev/null 2>&1 && echo "already installed" || curl -LsSf https://astral.sh/uv/install.sh
   # Verify installation
   uv --version
   ```

2. **Set up virtual environment**

   A "virtual environment" is a self-contained directory that contains the Python
   version you have chosen, along with the packages required by your project.
   This allows you to manage dependencies for your project without affecting (or
   being affected by) other Python projects on your system.

   The following command creates a virtual environment with a specific python version
   (in this example `3.13`)
   ```sh
   # Install the python version if needed, and set for this project.
   uv python install 3.13
   uv python pin 3.13
   # Create the virtual environment
   uv venv
   # Enter the virtual environment, and install dependencies
   source .venv/bin/activate
   uv sync
   ```

## Running your code

Whenever you want to run your code, make sure you are in the virtual environment.  To
enter the virtual environment, run:

```bash
source .venv/bin/activate
```

To run your Python code, you can use the following command:

```bash
python src/my_script.py
```

## Managing Dependencies

### Adding and removing dependencies

```bash
# Add a single package
uv add requests
# Add multiple packages
uv add pandas numpy matplotlib
# Add a specific version
uv add "django>=4.2"

### Remove Dependencies

```bash
# Remove a package
uv remove requests

# Remove a dev dependency
uv remove --dev pytest
```

### Update Dependencies

```bash
# Update all packages to latest compatible versions
uv lock --upgrade

# Update a specific package
uv add --upgrade requests
```


## Project Structure

```
your-project/
├── .python-version     # Pinned Python version
├── pyproject.toml      # Project metadata and dependencies
├── uv.lock            # Locked dependency versions
├── .venv/             # Virtual environment (git-ignored)
├── .gitignore         # Git ignore rules
├── README.md          # This file
└── src/               # Your source code
    └── ...
```

## Quick Command Reference

| Task                     | Command                     |
| ------------------------ | --------------------------- |
| Add a package            | `uv add package-name`       |
| Add a dev package        | `uv add --dev package-name` |
| Remove a package         | `uv remove package-name`    |
| Install all dependencies | `uv sync`                   |
| Install without dev deps | `uv sync --no-dev`          |
| Update lock file         | `uv lock`                   |
| Show installed packages  | `uv pip list`               |
