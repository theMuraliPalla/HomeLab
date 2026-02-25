# Python & PIP Commands Reference

Essential Python and PIP commands for development and DevOps.

---

## Python Execution
- `python --version` - Show Python version
- `python script.py` - Run Python script
- `python -m module` - Run module as script
- `python -c "print('hello')"` - Execute Python code directly
- `python -i script.py` - Run script in interactive mode
- `python -u script.py` - Run with unbuffered output (useful for logs)

## Python Interactive
- `python` - Start Python REPL/interactive shell
- `exit()` or `Ctrl+D` - Exit interactive shell
- `help(function)` - Get help on function/module
- `dir(object)` - List object attributes

## PIP - Package Management
- `pip --version` - Show pip version
- `pip install <package>` - Install package
- `pip install <package>==1.0.0` - Install specific version
- `pip install -r requirements.txt` - Install from requirements file
- `pip uninstall <package>` - Uninstall package
- `pip list` - List installed packages
- `pip show <package>` - Show package details
- `pip freeze` - Output installed packages in requirements format
- `pip freeze > requirements.txt` - Export dependencies to file
- `pip install --upgrade <package>` - Upgrade package
- `pip install --upgrade pip` - Upgrade pip itself
- `pip search <term>` - Search PyPI (deprecated, use web)

## Virtual Environments (venv)
- `python -m venv myenv` - Create virtual environment
- `myenv\Scripts\activate` - Activate venv (Windows)
- `source myenv/bin/activate` - Activate venv (Linux/Mac)
- `deactivate` - Deactivate virtual environment
- `which python` - Show which Python is being used (Linux/Mac)
- `where python` - Show which Python is being used (Windows)

## Virtual Environments (virtualenv)
- `pip install virtualenv` - Install virtualenv
- `virtualenv myenv` - Create virtual environment
- `virtualenv -p python3.9 myenv` - Create with specific Python version

## Package Building & Distribution
- `pip install -e .` - Install package in editable/development mode
- `python setup.py sdist` - Create source distribution
- `python setup.py bdist_wheel` - Create wheel distribution
- `pip wheel .` - Build wheel for current project
- `twine upload dist/*` - Upload package to PyPI

## Dependency Management
- `pip check` - Verify installed packages have compatible dependencies
- `pip list --outdated` - Show outdated packages
- `pip install --upgrade-strategy eager <package>` - Upgrade with dependencies
- `pipdeptree` - Show dependency tree (install first)

## Python Path & Modules
- `python -m site` - Show site-packages location
- `python -c "import sys; print(sys.path)"` - Show Python search path
- `python -c "import module; print(module.__file__)"` - Find module location

## Testing & Code Quality
- `python -m pytest` - Run tests with pytest
- `python -m unittest discover` - Run unit tests
- `python -m pylint script.py` - Lint Python code
- `python -m black script.py` - Format code with Black
- `python -m flake8 script.py` - Check style guide
- `python -m mypy script.py` - Type checking

## Performance & Debugging
- `python -m timeit "code"` - Measure execution time
- `python -m cProfile script.py` - Profile script performance
- `python -m pdb script.py` - Debug script with pdb
- `python -m trace --trace script.py` - Trace execution

## HTTP Server
- `python -m http.server` - Start HTTP server on port 8000
- `python -m http.server 8080` - Start on specific port

## JSON Processing
- `python -m json.tool file.json` - Pretty-print JSON
- `echo '{"key":"value"}' | python -m json.tool` - Format JSON from pipe

## Environment & System
- `python -c "import os; print(os.environ)"` - Show environment variables
- `python -c "import platform; print(platform.system())"` - Show OS info
- `python -c "import sys; print(sys.executable)"` - Show Python executable path

## Common DevOps Patterns
- `pip install --no-cache-dir <package>` - Install without cache (Docker)
- `pip install --user <package>` - Install for current user only
- `pip download <package>` - Download package without installing
- `pip install --proxy http://proxy:port <package>` - Install via proxy
- `pip config list` - Show pip configuration
- `pip config set global.index-url <url>` - Set custom PyPI mirror

## Requirements File Management
- `pip freeze | grep <package>` - Find specific package version
- `pip install -r requirements.txt --upgrade` - Upgrade all packages
- `pip-compile requirements.in` - Generate locked requirements (pip-tools)

## Alternative Package Managers
- `poetry install` - Install dependencies (Poetry)
- `poetry add <package>` - Add package (Poetry)
- `pipenv install` - Install from Pipfile (Pipenv)
- `pipenv install <package>` - Add package (Pipenv)
- `conda install <package>` - Install with Conda

## Useful One-Liners
- `python -m venv venv && source venv/bin/activate && pip install -r requirements.txt` - Setup project
- `pip list --format=freeze > requirements.txt` - Export clean requirements
- `pip install --quiet --upgrade pip setuptools wheel` - Update build tools

## Bonus: Date/Time Function
```python
from datetime import datetime

def get_formatted_datetime():
    """Returns current date and time in dd-mm-yyyy HH:MM:SS format"""
    return datetime.now().strftime("%d-%m-%Y %H:%M:%S")

def get_formatted_date():
    """Returns current date in dd-mm-yyyy format"""
    return datetime.now().strftime("%d-%m-%Y")

# Example usage
print(get_formatted_datetime())  # Output: 25-02-2026 14:30:45
```

**Common format codes:**
- `%d` - Day (01-31), `%m` - Month (01-12), `%Y` - Year (4 digits)
- `%H` - Hour 24h (00-23), `%I` - Hour 12h (01-12)
- `%M` - Minute (00-59), `%S` - Second (00-59)
- `%p` - AM/PM, `%f` - Microsecond

---

**Last Updated:** February 25, 2026
