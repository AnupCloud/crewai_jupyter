# CrewAI + Anthropic Prompt Caching Cookbook

🚀 **Advanced cost optimization and performance enhancement for CrewAI agents using Anthropic's prompt caching capabilities.**

**Repository**: https://github.com/AnupCloud/crewai_jupyter.git

## 📋 Overview

This comprehensive cookbook demonstrates how to:
- **Implement a custom CrewAI LLM** that integrates with Anthropic's Messages API
- **Leverage prompt caching** for up to 90% cost reduction and 85% faster responses
- **Process large documents efficiently** with persistent system context caching
- **Monitor cache performance** with built-in metrics and token tracking
- **Optimize production workflows** with configurable cache TTL settings

## 🎯 Why This Cookbook Matters

### **💰 Cost Optimization:**
- **Reduce API costs by up to 90%** for repeated queries with cached content
- **Cached tokens cost only 10%** of regular input tokens
- **Ideal for document analysis**, multi-turn conversations, and reference-heavy tasks

### **⚡ Performance Enhancement:**
- **Speed up response times by 50-85%** on cache hits
- **Minimize latency** for frequently accessed system contexts
- **Optimize throughput** for high-volume agent workflows

### **🎮 Real-World Applications:**
- **Legal document review** with cached contract templates
- **Customer support** with cached policy documents
- **Educational tutoring** with cached textbook content
- **Research analysis** with cached reference materials

## Prompt caching flow

![Prompt caching flow](prompt_caching_flow.png)

## ✨ Key Features

### **🏗️ Custom LLM Implementation**
- **Extends CrewAI's `BaseLLM`** for seamless integration
- **Anthropic Messages API** with full caching support
- **Production-ready error handling** and timeout management
- **Flexible cache configuration** with TTL options

### **📊 Advanced Monitoring**
- **Real-time cache metrics** (read/write tokens)
- **Performance benchmarking** (execution time comparisons)
- **Cost analysis** (token usage and savings calculations)
- **Debug-friendly logging** for optimization insights

### **📚 Document Processing**
- **Large text handling** (Frankenstein novel ~446K characters)
- **Smart content truncation** for context window management  
- **Literary analysis use case** with cached reference materials
- **Scalable to any document type** (legal, technical, educational)

## 📋 Prerequisites

- **Python 3.9+** with pip installed
- **Anthropic API key** with access to Claude models  
- **Internet access** for fetching public domain texts
- **Jupyter Notebook** environment

## 🚀 Quick Setup

### **1. Environment Setup**
```bash
# From the main project directory
cd /path/to/crewai_jupyter

# Activate virtual environment
source .venv_manual/bin/activate  # macOS/Linux
# or .venv_manual\Scripts\activate  # Windows
```

### **2. Install Dependencies**
```bash
# Install prompt caching specific requirements
pip install -r Prompt_Caching/requirements.txt

# Core dependencies include:
# - crewai[tools]
# - anthropic  
# - requests
# - jupyter
# - ipython
```

### **3. Configure API Key**
Add to your `.env` file in the project root:
```bash
ANTHROPIC_API_KEY=your_anthropic_api_key_here
```

**Get your API key**: https://console.anthropic.com/

## 📖 How to Use

### **1. Launch Notebook**
```bash
# From the project root
jupyter notebook

# Navigate to: Prompt_Caching/crewai_anthropic_prompt_caching_cookbook.ipynb
```

### **2. Follow the Workflow**
1. **Environment setup** - Import libraries and configure API key
2. **Custom LLM creation** - Instantiate the caching-enabled LLM
3. **Document fetching** - Download Frankenstein text from Project Gutenberg  
4. **Agent configuration** - Create literary analysis agent
5. **Performance testing** - Run queries and observe cache behavior

### **3. Monitor Results**
- **First run**: Watch cache write tokens and execution time
- **Second run**: Observe cache hit and performance improvement
- **Cost analysis**: Compare token usage and cost savings

## 🔧 Key Components

### **📦 AnthropicPromptCachingLLM Class**
```python
class AnthropicPromptCachingLLM(BaseLLM):
    def __init__(
        self,
        model: str = "claude-sonnet-4-20250514",
        cache_ttl: str = "5m",  # "5m" or "1h"
        system_content: List[Dict] = None,
        extended_ttl_beta_header: str = None,
    ):
        # Initialize with cache configuration
        
    def call(self, messages, **kwargs):
        # Add cache control to system content
        # Track cache read/write metrics
        # Return assistant response
```

### **⏰ Cache TTL Options**

#### **Default 5-Minute TTL**
- ✅ **No beta access required**
- ✅ **Automatic cache management**  
- ✅ **Ideal for development and testing**
- ⏱️ **5-minute cache duration**

#### **Extended 1-Hour TTL (Beta)**
- 🔐 **Requires beta access from Anthropic**
- 📧 **Need specific header value**
- 🏭 **Ideal for production workloads**
- ⏱️ **1-hour cache duration**

## 📈 Performance Benefits

### **💰 Cost Savings Analysis**
```python
# Example: 100K token document analysis
Standard Approach:
├─ Query 1: 100K input + 1K output = $1.50
├─ Query 2: 100K input + 1K output = $1.50  
└─ Total: $3.00

With Prompt Caching:
├─ Query 1: 100K input (cached) + 1K output = $1.50
├─ Query 2: 10K cached read + 1K output = $0.35
└─ Total: $1.85 (38% cost reduction)
```

### **⚡ Speed Improvements**
- **First Run** (Cache Write): Baseline response time + cache creation
- **Subsequent Runs** (Cache Hit): 50-85% faster response times
- **Token Processing**: Dramatic reduction in input token processing time

### **📊 Real Metrics from Notebook**
```bash
First run time: 12.45s
Cache Write: Wrote 75,324 tokens to cache.

Second run time: 4.23s  
Cache Hit: Read 75,324 tokens from cache.

Performance gain: 66% faster execution
Cost savings: 90% reduction in input token costs
```

## 🎯 Use Cases & Applications

### **📄 Document Analysis**
```python
# Legal contract review
system_content = [
    {"type": "text", "text": "You are a legal contract analyst..."},
    {"type": "text", "text": contract_template_content}  # Gets cached
]

# Research paper analysis  
system_content = [
    {"type": "text", "text": "You are a research analyst..."},
    {"type": "text", "text": reference_papers_content}  # Gets cached
]
```

### **🎓 Educational Applications**
- **Textbook tutoring**: Cache entire chapters for student Q&A
- **Literature analysis**: Cache novels/poems for literary discussion
- **Historical research**: Cache primary source documents
- **Scientific learning**: Cache research papers and textbooks

### **💼 Business Applications**
- **Policy consultation**: Cache employee handbooks and policies
- **Brand compliance**: Cache style guides and brand documentation
- **Technical support**: Cache product manuals and troubleshooting guides
- **Training materials**: Cache course content for interactive learning

## 🔧 Troubleshooting Guide

### **🚨 Common Issues & Solutions**

#### **Context Window Errors**
```python
# Problem: Document too large for model context
# Solution: Adjust maximum character limit
MAX_CHARS_FOR_DEMO = 200_000  # Reduce this value
text = text[:MAX_CHARS_FOR_DEMO] if len(text) > MAX_CHARS_FOR_DEMO else text
```

#### **No Cache Logs Appearing**
```python
# Problem: Not seeing cache read/write messages
# Checklist:
✅ Second query within TTL window (5 minutes or 1 hour)
✅ System content unchanged between queries
✅ Same LLM instance used for both queries
✅ API key valid and model accessible
```

#### **1-Hour TTL Not Working**
```python
# Problem: Extended TTL not available
# Requirements for 1-hour TTL:
🔐 Beta access from Anthropic
📧 Specific anthropic-beta header value
🏷️ Contact Anthropic support for beta access

# Example configuration:
llm = AnthropicPromptCachingLLM(
    cache_ttl="1h",
    extended_ttl_beta_header="extended-cache-ttl-2025-04-11"  # Your beta value
)
```

#### **API Authentication Errors**
```python
# Debug commands:
import os
print("API Key configured:", bool(os.getenv("ANTHROPIC_API_KEY")))
print("Key length:", len(os.getenv("ANTHROPIC_API_KEY", "")))

# Common solutions:
✅ Verify API key in .env file
✅ Restart Jupyter kernel after adding key
✅ Check key has Claude model access
✅ Verify no extra spaces in key
```

## 🎓 Advanced Patterns & Best Practices

### **🔄 Multi-Document Caching**
```python
# Cache multiple reference documents
system_blocks = [
    {"type": "text", "text": "You are a comprehensive analyst..."},
    {"type": "text", "text": legal_document_1},
    {"type": "text", "text": technical_manual_2},
    {"type": "text", "text": policy_document_3},  # Last block gets cached
]
```

### **📊 Cache Efficiency Monitoring**
```python
def analyze_cache_performance(results):
    """Monitor cache hit rates and cost savings"""
    total_queries = len(results)
    cache_hits = sum(1 for r in results if r.cache_read_tokens > 0)
    efficiency = (cache_hits / total_queries) * 100
    
    print(f"Cache Hit Rate: {efficiency:.1f}%")
    print(f"Total Queries: {total_queries}")
    print(f"Cache Hits: {cache_hits}")
    return efficiency

# Usage
performance_data = []
for query in test_queries:
    result = crew.kickoff(inputs={"query": query})
    performance_data.append(result)

efficiency = analyze_cache_performance(performance_data)
```

### **💡 Production Optimization Tips**

#### **Cache Strategy**
- **Group similar queries** within cache TTL windows
- **Use 1-hour TTL** for production workloads when available
- **Monitor cache hit rates** to optimize query patterns
- **Batch related questions** to maximize cache utilization

#### **Content Management**
- **Place largest/most expensive content last** in system blocks
- **Keep cached content under context limits** (~200K tokens)
- **Use consistent formatting** to ensure cache hits
- **Preprocess documents** for optimal token usage

#### **Cost Management**
```python
# Track costs across cache windows
class CacheAnalyzer:
    def __init__(self):
        self.total_input_tokens = 0
        self.cached_read_tokens = 0
        self.cache_write_tokens = 0
        
    def log_usage(self, result):
        usage = result.get("usage", {})
        self.cached_read_tokens += usage.get("cache_read_input_tokens", 0)
        self.cache_write_tokens += usage.get("cache_creation_input_tokens", 0)
        
    def cost_summary(self):
        cache_savings = (self.cached_read_tokens * 0.9)  # 90% savings
        print(f"Cache read tokens: {self.cached_read_tokens:,}")
        print(f"Estimated savings: ${cache_savings * 0.000015:.2f}")
```

## 📚 Related Resources

### **Documentation**
- **Anthropic API Docs**: https://docs.anthropic.com/
- **CrewAI Documentation**: https://docs.crewai.com/
- **Prompt Caching Guide**: https://docs.anthropic.com/en/docs/prompt-caching

### **External Resources**
- **Project Gutenberg**: https://www.gutenberg.org/ (public domain texts)
- **Main Repository**: https://github.com/AnupCloud/crewai_jupyter.git
- **Anthropic Console**: https://console.anthropic.com/

### **Model Information**
- **Supported Models**: Claude 3 Haiku, Claude 3 Sonnet, Claude 3 Opus, Claude 3.5 Sonnet
- **Cache Pricing**: Cached tokens cost 10% of regular input tokens
- **Context Windows**: Up to 200K tokens depending on model

## 🚀 Next Steps

After mastering this cookbook, consider:

1. **Implement in Production**: Use caching in your own CrewAI workflows
2. **Experiment with Content**: Try different document types and sizes
3. **Optimize Costs**: Monitor cache hit rates and adjust strategies
4. **Scale Up**: Build multi-agent systems with shared cached knowledge
5. **Custom Integrations**: Adapt the LLM class for your specific needs

## 🤝 Contributing

We welcome contributions to improve this cookbook:

- **Bug Reports**: Submit issues for any problems encountered
- **Feature Requests**: Suggest improvements or new examples
- **Code Contributions**: Submit pull requests with enhancements
- **Documentation**: Help improve setup and usage instructions

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- **Mary Shelley's "Frankenstein"**: Public domain text from Project Gutenberg
- **Anthropic**: For providing advanced prompt caching capabilities
- **CrewAI**: For the excellent multi-agent framework
- **Community**: For feedback and contributions

---

**Built with passion for AI cost optimization and performance enhancement. Happy caching! 🚀**
