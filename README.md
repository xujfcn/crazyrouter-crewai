# CrewAI with Crazyrouter

Updated 2026-10-12. Configure the LLM explicitly so that agent calls use the intended gateway.

```bash
pip install crewai
export CRAZYROUTER_API_KEY="YOUR_CRAZYROUTER_API_KEY"
```

```python
import os
from crewai import Agent, Task, Crew, Process, LLM

llm = LLM(
    model="openai/gpt-4o-mini",
    api_key=os.environ["CRAZYROUTER_API_KEY"],
    base_url="https://crazyrouter.com/v1",
)
writer = Agent(
    role="Technical writer",
    goal="Explain technical concepts clearly",
    backstory="A writer of concise developer documentation",
    llm=llm,
)
task = Task(
    description="Explain what an API gateway does in three sentences.",
    expected_output="Three clear sentences",
    agent=writer,
)
crew = Crew(agents=[writer], tasks=[task], process=Process.sequential)
print(crew.kickoff())
```

Here `openai/` selects CrewAI's OpenAI provider; the model sent over the wire must be `gpt-4o-mini`. Do not copy the provider prefix into direct Crazyrouter REST requests. For a custom Claude/Gemini model, verify the installed CrewAI provider behavior and the model's tool support before using an agent team.

This minimal task performs no web search. A research task does not acquire browsing capability merely because its prompt says “research”; configure and verify an appropriate tool separately.

[CrewAI documentation](https://docs.crewai.com) · [Current prices](https://crazyrouter.com/en/pricing) · [API documentation](https://docs.crazyrouter.com)
