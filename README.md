# 🚢 CrewAI + Crazyrouter Setup Guide

> Build AI agent crews with CrewAI, powered by Crazyrouter — Save 45%.

[Crazyrouter](https://crazyrouter.com?ref=github) — One API key, 300+ models.

## 💰 Price Comparison

| Model | Official (In/Out per 1M tokens) | Crazyrouter | Savings |
|-------|--------------------------------|-------------|---------|
| GPT-4o | $2.50 / $10 | $1.38 / $5.50 | **45%** |
| Claude Sonnet 4 | $3 / $15 | $1.65 / $8.25 | **45%** |
| Claude Opus 4 | $15 / $75 | $8.25 / $41.25 | **45%** |

## ⚡ Quick Start

### Installation
```bash
pip install crewai crewai-tools
```

### Environment Setup
```bash
export OPENAI_API_KEY=sk-your-crazyrouter-key
export OPENAI_API_BASE=https://crazyrouter.com/v1
```

### Basic Crew
```python
import os
os.environ["OPENAI_API_KEY"] = "sk-your-crazyrouter-key"
os.environ["OPENAI_API_BASE"] = "https://crazyrouter.com/v1"

from crewai import Agent, Task, Crew, Process

# Define agents
researcher = Agent(
    role="Senior Research Analyst",
    goal="Find comprehensive information about AI API pricing",
    backstory="Expert at analyzing tech markets and pricing strategies",
    llm="gpt-4o",
    verbose=True
)

writer = Agent(
    role="Content Writer",
    goal="Write engaging blog posts based on research",
    backstory="Experienced tech writer with a knack for simplifying complex topics",
    llm="gpt-4o",
    verbose=True
)

# Define tasks
research_task = Task(
    description="Research the current AI API pricing landscape, comparing major providers",
    expected_output="Detailed pricing comparison report",
    agent=researcher
)

writing_task = Task(
    description="Write a blog post about AI API pricing based on the research",
    expected_output="A 1000-word blog post",
    agent=writer
)

# Create and run crew
crew = Crew(
    agents=[researcher, writer],
    tasks=[research_task, writing_task],
    process=Process.sequential,
    verbose=True
)

result = crew.kickoff()
print(result)
```

### Mixed Models Crew
```python
# Use different models for different agents
analyst = Agent(role="Analyst", llm="claude-sonnet-4-20250514")  # Claude for analysis
coder = Agent(role="Coder", llm="gpt-4o")  # GPT for coding
reviewer = Agent(role="Reviewer", llm="claude-opus-4-20250514")  # Opus for review

# All through one Crazyrouter key!
```

## ❓ FAQ

**Q: Does CrewAI work with Crazyrouter?**
A: Yes, set OPENAI_API_BASE to Crazyrouter URL.

**Q: Can agents use different models?**
A: Yes! Specify different model IDs per agent.

**Q: Do CrewAI tools work?**
A: Yes, all tools work independently of the LLM provider.

## 🔗 Links
- 🌐 [Crazyrouter](https://crazyrouter.com?ref=github)
- 🚢 [CrewAI](https://github.com/crewAIInc/crewAI)
- 💬 [Telegram](https://t.me/crzrouter)

## 📄 License
MIT

