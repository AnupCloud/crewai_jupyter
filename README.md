# CrewAI Complete Ecosystem - Advanced AI Agent Systems

🚀 **Repository**: https://github.com/AnupCloud/crewai_jupyter.git

This comprehensive project demonstrates CrewAI's complete ecosystem through 5 advanced Jupyter notebooks covering collaboration, reasoning, planning, guardrails, and prompt caching with multiple LLM providers.

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

Before running the notebooks, you'll need:

1. **OpenAI API Key** - Get from https://platform.openai.com/api-keys
2. **EXA API Key** - Get from https://exa.ai/
3. **Google Gemini API Key** - Get from https://makersuite.google.com/app/apikey
4. **Anthropic API Key** - Get from https://console.anthropic.com/
5. **SerperDev API Key** - Get from https://serper.dev/ (for guardrails notebook)

Create a `.env` file in the project root:
```bash
OPENAI_API_KEY=your_openai_key_here
EXA_API_KEY=your_exa_key_here
GEMINI_API_KEY=your_gemini_key_here
ANTHROPIC_API_KEY=your_anthropic_key_here
SERPER_API_KEY=your_serper_key_here
```

## Project Structure After Setup

```
crew_ai_project/
├── Collaboration/
│   └── crewai_collaboration.ipynb        # Multi-agent collaboration patterns
├── Reasoning/
│   └── crewai_reasoning.ipynb           # Agent reasoning capabilities
├── Planning/
│   └── crewai_planning.ipynb            # Strategic task planning
├── Guardrails/
│   └── task_guardrails.ipynb            # Quality control & validation
├── Prompt_Caching/
│   ├── crewai_anthropic_prompt_caching_cookbook.ipynb  # Anthropic prompt caching
│   └── requirements.txt                  # Prompt caching dependencies
├── .venv_manual/                        # Virtual environment
├── .env                                # API keys (create this)
├── .gitignore                          # Git ignore rules
├── pyproject.toml                      # UV configuration
├── uv.lock                            # UV lock file
├── main.py                            # Python script version
├── README.md                          # This comprehensive guide
├── README_SETUP.md                    # Detailed setup guide
└── LinkedIn_Post_All4_Notebooks.md    # Marketing content
```

## 📚 Notebook Overview

### 🤝 **1. Collaboration (`Collaboration/crewai_collaboration.ipynb`)**
- **Single Task Collaboration**: Multiple agents working together on one task
- **Sequential Pipeline**: Structured Research → Write → Edit workflow
- **Hierarchical Management**: Manager-led team coordination
- **Tools**: EXA Search, OpenAI GPT-4, delegation mechanisms

### 🧠 **2. Reasoning (`Reasoning/crewai_reasoning.ipynb`)**
- **Step-by-step thinking** with `reasoning=True`
- **Gemini model integration** for enhanced reasoning
- **Multi-attempt reasoning** with configurable limits
- **60% quality improvement** through thoughtful task planning

### 📋 **3. Planning (`Planning/crewai_planning.ipynb`)**
- **AgentPlanner integration** for strategic task orchestration
- **Pre-execution planning** with dedicated planning LLM
- **Alternative to reasoning** for complex project workflows
- **Enhanced task descriptions** through automated planning

### 🛡️ **4. Guardrails (`Guardrails/task_guardrails.ipynb`)**
- **Custom validation functions** for quality control
- **Production-ready safeguards** for customer support scenarios
- **Multi-criteria validation** (word count, tone, content, compliance)
- **Automatic retry mechanisms** for failed validations

### 🚀 **5. Prompt Caching (`Prompt_Caching/crewai_anthropic_prompt_caching_cookbook.ipynb`)**
- **Anthropic Claude integration** with custom LLM implementation
- **Prompt caching optimization** for cost reduction and performance
- **Literary analysis use case** with large document processing
- **Cache metrics monitoring** for read/write token tracking
- **5-minute and 1-hour TTL options** for different use cases

## 🛠️ Technology Stack

### **Core Framework**
- **CrewAI**: Multi-agent orchestration and workflow management
- **Python 3.8+**: Programming language
- **Jupyter Notebooks**: Interactive development environment

### **LLM Providers**
- **OpenAI GPT-4**: Primary language model for most agents
- **Google Gemini**: Optimized for reasoning tasks
- **Anthropic Claude**: Advanced prompt caching capabilities

### **Tools & APIs**
- **EXA Search**: Real-time web research and data gathering
- **SerperDev**: Alternative search with SERP results
- **ScrapeWebsite Tool**: Website content extraction

### **Development Environment**
- **python-dotenv**: Secure API key management
- **UV Package Manager**: Modern Python dependency management
- **Virtual Environment**: Isolated Python environment

## 🚀 Quick Start

1. **Clone the repository:**
```bash
git clone https://github.com/AnupCloud/crewai_jupyter.git
cd crewai_jupyter
```

2. **Set up virtual environment:**
```bash
python3 -m venv .venv_manual
source .venv_manual/bin/activate  # macOS/Linux
# or .venv_manual\Scripts\activate  # Windows
```

3. **Install dependencies:**
```bash
pip install crewai crewai-tools exa_py python-dotenv jupyter ipywidgets anthropic
```

4. **Configure API keys in `.env` file**

5. **Start exploring:**
```bash
jupyter notebook
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
