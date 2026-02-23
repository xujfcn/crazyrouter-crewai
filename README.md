# 🚢 CrewAI + Crazyrouter

> Build AI agent crews with CrewAI, powered by Crazyrouter.

## ⚡ Setup
```python
import os
os.environ["OPENAI_API_KEY"] = "sk-your-crazyrouter-key"
os.environ["OPENAI_API_BASE"] = "https://crazyrouter.com/v1"

from crewai import Agent, Task, Crew

researcher = Agent(role="Researcher", goal="Find information", llm="gpt-4o")
writer = Agent(role="Writer", goal="Write content", llm="claude-sonnet-4-20250514")

task = Task(description="Research and write about API gateways", agent=researcher)
crew = Crew(agents=[researcher, writer], tasks=[task])
result = crew.kickoff()
```

## 🔗 [Crazyrouter](https://crazyrouter.com?ref=github) | [CrewAI](https://github.com/crewAIInc/crewAI)
## 📄 License: MIT
