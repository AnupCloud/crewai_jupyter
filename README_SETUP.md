# CrewAI Collaboration Project - Setup Guide

This project demonstrates CrewAI's agent collaboration features through interactive Jupyter notebooks.

## The Error We Encountered

When trying to install packages directly with pip, we encountered this error:

```
error: externally-managed-environment

× This environment is externally managed
╰─> To install Python packages system-wide, try brew install
    xyz, where xyz is the package you are trying to
    install.
    
    If you wish to install a Python library that isn't in Homebrew,
    use a virtual environment:
    
    python3 -m venv path/to/venv
    source path/to/venv/bin/activate
    python3 -m pip install xyz
```

**Why this happens:** macOS Python installations are "externally managed" to prevent system conflicts and maintain stability.

## Solution: Virtual Environment Setup

### Prerequisites

- Python 3.8 or higher
- macOS, Linux, or Windows
- Terminal/Command Prompt access

### Step 1: Create Virtual Environment

```bash
# Navigate to your project directory
cd /Users/anup/Desktop/Anup/crew_ai_project

# Create virtual environment
python3 -m venv .venv_manual
```

### Step 2: Activate Virtual Environment

**macOS/Linux:**
```bash
source .venv_manual/bin/activate
```

**Windows:**
```cmd
.venv_manual\Scripts\activate
```

**Verification:** Your prompt should now show `(.venv_manual)` at the beginning.

### Step 3: Install Dependencies

```bash
# Upgrade pip first (recommended)
pip install --upgrade pip

# Install required packages (this may take 5-10 minutes)
pip install crewai crewai-tools exa_py python-dotenv jupyter ipywidgets
```

### Step 4: Run the First Notebook Cell

```bash
# Execute the warning filter cell
python -c "
import warnings
warnings.filterwarnings('ignore', category=DeprecationWarning)
print('✅ Deprecation warnings filtered successfully!')
"
```

### Step 5: Start Jupyter Notebook

```bash
jupyter notebook
```

This will open your browser with the Jupyter interface. Navigate to `Collaboration/crewai_collaboration.ipynb` to start.

## Alternative: Using UV Package Manager

If your project already has `pyproject.toml` and `uv.lock` files:

### Install UV
```bash
# macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Or using Homebrew
brew install uv
```

### Use UV
```bash
# Sync dependencies
uv sync

# Run jupyter
uv run jupyter notebook
```

**Note:** UV installation can be slower and may timeout. The manual virtual environment method is more reliable.

## API Keys Setup

Before running the notebook, you'll need:

1. **OpenAI API Key** - Get from https://platform.openai.com/api-keys
2. **EXA API Key** - Get from https://exa.ai/

Create a `.env` file in the project root:
```bash
OPENAI_API_KEY=your_openai_key_here
EXA_API_KEY=your_exa_key_here
```

## Project Structure After Setup

```
crew_ai_project/
├── Collaboration/
│   └── crewai_collaboration.ipynb    # Main notebook
├── .venv_manual/                     # Virtual environment
├── .env                             # API keys (create this)
├── pyproject.toml                   # UV configuration
├── uv.lock                         # UV lock file
├── main.py                         # Python script
└── README.md                       # Original README
└── README_SETUP.md                 # This setup guide
```

## Troubleshooting Common Issues

### 1. "Command not found: python3"
- Try `python` instead of `python3`
- Verify Python installation: `python --version`

### 2. Virtual environment not activating
- Check the path: `ls .venv_manual/bin/` (should show `activate`)
- Try absolute path: `source /full/path/to/.venv_manual/bin/activate`

### 3. Packages failing to install
- Update pip: `pip install --upgrade pip`
- Install one by one: `pip install crewai`, then `pip install crewai-tools`, etc.
- Check internet connection

### 4. "ModuleNotFoundError" in Jupyter
- Ensure virtual environment is activated
- Reinstall packages in the virtual environment
- Restart Jupyter after installing packages

### 5. Jupyter notebook won't start
- Install jupyter: `pip install jupyter`
- Try different port: `jupyter notebook --port 8889`
- Check for conflicting processes

## Next Steps

1. ✅ Virtual environment created and activated
2. ✅ Dependencies installed
3. ✅ First cell executed (warning filters)
4. 🔄 Configure API keys in `.env` file
5. 🔄 Open Jupyter notebook
6. 🔄 Run remaining notebook cells

## Verification Commands

To verify your setup is working:

```bash
# Check virtual environment is active
which python  # Should show path to .venv_manual

# Check packages are installed
python -c "import crewai; print('CrewAI installed successfully')"

# Check Jupyter is working
jupyter --version
```

## Success Indicators

- ✅ Terminal prompt shows `(.venv_manual)`
- ✅ `pip list` shows crewai, crewai-tools, exa_py
- ✅ Warning filter cell executed successfully
- ✅ Jupyter notebook opens without errors

This setup method resolves the "externally-managed-environment" error by creating an isolated Python environment specifically for this project.