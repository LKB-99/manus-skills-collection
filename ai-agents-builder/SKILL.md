
---
name: ai-agents-builder
description: Create autonomous AI agents using frameworks like LangChain, AutoGPT, and CrewAI.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# AI Agents Builder

## Overview
This skill empowers you to build, customize, and deploy autonomous AI agents. Leveraging powerful frameworks like LangChain, AutoGPT, and CrewAI, you can create sophisticated agents capable of complex reasoning, tool use, and collaborative task execution. Whether you're a developer looking to integrate AI into your applications or a researcher exploring the frontiers of agentic AI, this skill provides the necessary tools and knowledge to bring your ideas to life.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

- **Automating Complex Workflows:** Create agents that can handle multi-step tasks, such as conducting research, generating reports, and writing code.
- **Building Intelligent Applications:** Integrate AI agents into your web apps, SaaS platforms, or other software to provide intelligent features and services.
- **Prototyping and Research:** Quickly prototype and experiment with different agent architectures, reasoning models, and collaborative strategies.
- **Personal Assistants:** Develop personalized AI assistants that can help you with your daily tasks, such as managing your schedule, answering emails, and providing information.
- **Customer Support Automation:** Build AI-powered customer support agents that can handle a wide range of customer inquiries and issues.

## Core Capabilities
This skill provides a comprehensive set of capabilities for building and managing AI agents:

### 1. Framework Integration
- **LangChain:** A modular framework for building LLM-powered applications. It provides a rich set of tools for chaining LLM calls, managing memory, and integrating with external data sources.
- **AutoGen:** A multi-agent conversation framework developed by Microsoft. It enables you to build and orchestrate multiple agents that can collaborate to solve complex tasks.
- **CrewAI:** A role-based task execution engine that simplifies the creation of collaborative AI agents. It allows you to define agents with specific roles and responsibilities and have them work together as a crew.

### 2. Agent Customization
- **Role-Based Agents:** Define agents with specific roles, goals, and backstories to create more human-like and specialized agents.
- **Tool Integration:** Equip your agents with a wide range of tools, including web search, code execution, and database access, to extend their capabilities.
- **Memory Management:** Implement both short-term and long-term memory for your agents, allowing them to learn from past interactions and maintain context.

### 3. Collaborative Workflows
- **Multi-Agent Systems:** Build and manage multi-agent systems where agents can communicate, collaborate, and delegate tasks to solve complex problems.
- **Human-in-the-Loop:** Seamlessly integrate human feedback and oversight into your agentic workflows to ensure safety and reliability.
- **Task Orchestration:** Define and manage complex task workflows, including sequential, parallel, and conditional execution.

## Step-by-Step Workflow
This section provides a step-by-step guide to creating AI agents using LangChain, AutoGPT, and CrewAI.

### 1. Building an Agent with LangChain
LangChain provides a flexible and modular approach to building AI agents. Here's how you can create a simple research agent:

**Step 1: Install LangChain and required libraries**
```bash
pip install langchain langchain-openai
```

**Step 2: Set up your environment**
```python
import os

# Set your OpenAI API key
os.environ["OPENAI_API_KEY"] = "your-openai-api-key"
```

**Step 3: Define tools for the agent**
Tools are functions that an agent can use to interact with the outside world.
```python
from langchain.agents import Tool
from langchain_community.utilities import SerpAPIWrapper

search = SerpAPIWrapper()

tools = [
    Tool.from_function(
        func=search.run,
        name="Search",
        description="Useful for when you need to answer questions about current events"
    )
]
```

**Step 4: Initialize the agent**
We will use the `zero-shot-react-description` agent type, which is a general-purpose action-based agent.
```python
from langchain.agents import initialize_agent
from langchain.agents.agent_types import AgentType
from langchain_openai import OpenAI

llm = OpenAI(temperature=0)

agent = initialize_agent(
    tools,
    llm,
    agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
    verbose=True
)
```

**Step 5: Run the agent**
```python
agent.run("What is the latest news on AI?")
```

### 2. Setting up a Task with AutoGPT
AutoGPT is designed for autonomous task execution. It takes a high-level goal and breaks it down into smaller, manageable tasks.

**Step 1: Clone the AutoGPT repository**
```bash
git clone https://github.com/Significant-Gravitas/Auto-GPT.git
cd Auto-GPT
```

**Step 2: Install dependencies**
```bash
pip install -r requirements.txt
```

**Step 3: Configure AutoGPT**
Rename `.env.template` to `.env` and add your OpenAI API key.

**Step 4: Run AutoGPT**
```bash
python -m autogpt
```
AutoGPT will then prompt you to define a task for your AI agent. For example:

`Name your AI: ResearchGPT`
`ResearchGPT is: an AI designed to research and write a report on the future of AI.`
`Goal 1: Research the latest trends in AI for 2026.`
`Goal 2: Identify the key players and their contributions.`
`Goal 3: Write a 500-word report on the findings.`
`Goal 4: Save the report to a file named 'ai_report.txt'.`
`Goal 5: Terminate when the report is complete.`

### 3. Creating a Crew with CrewAI
CrewAI excels at orchestrating multi-agent systems where each agent has a specific role.

**Step 1: Install CrewAI**
```bash
pip install crewai
```

**Step 2: Define your agents**
Each agent has a role, a goal, and a backstory.
```python
from crewai import Agent

researcher = Agent(
  role='Senior Research Analyst',
  goal='Uncover cutting-edge developments in AI and data science',
  backstory=('You are a Senior Research Analyst at a top tech think tank. ' 
             'Your expertise lies in identifying emerging trends. ' 
             'You have a knack for dissecting complex data and presenting actionable insights.'),
  verbose=True,
  allow_delegation=False
)

writer = Agent(
  role='Tech Content Strategist',
  goal='Craft compelling content on tech advancements',
  backstory=('You are a renowned Tech Content Strategist, known for your insightful and engaging articles. ' 
             'You transform complex concepts into compelling narratives.'),
  verbose=True,
  allow_delegation=True
)
```

**Step 3: Define tasks for your agents**
```python
from crewai import Task

task1 = Task(
  description=('Conduct a comprehensive analysis of the latest advancements in AI in 2026. ' 
               'Identify key trends, breakthrough technologies, and potential industry impacts.'),
  expected_output='A full analysis report with detailed insights.',
  agent=researcher
)

task2 = Task(
  description=('Using the insights provided, write a blog post that highlights the most significant AI advancements. ' 
               'Your post should be informative yet accessible, catering to a tech-savvy audience. ' 
               'Make it sound cool, avoid complex words so it doesn\'t sound like AI.'),
  expected_output='A 1000-word blog post in markdown format.',
  agent=writer
)
```

**Step 4: Assemble your crew and run the tasks**
```python
from crewai import Crew, Process

crew = Crew(
  agents=[researcher, writer],
  tasks=[task1, task2],
  process=Process.sequential # Tasks will be executed one after the other
)

result = crew.kickoff()

print("######################")
print(result)
```
## Best Practices
To build effective and reliable AI agents, consider the following best practices:

- **Start with a Clear Goal:** Define a clear and specific goal for your agent. This will help you to design the agent's role, tools, and tasks more effectively.
- **Choose the Right Framework:** Select the framework that best suits your needs. LangChain is great for custom workflows, AutoGPT is ideal for autonomous task execution, and CrewAI is perfect for collaborative multi-agent systems.
- **Design Specialized Agents:** Instead of creating a single, general-purpose agent, consider building a team of specialized agents with distinct roles and responsibilities. This will lead to more robust and efficient task execution.
- **Provide Specific Instructions:** Give your agents clear and detailed instructions. The more specific you are, the better the agent will perform.
- **Use the Right Tools:** Equip your agents with the necessary tools to accomplish their tasks. This may include web search, code execution, database access, or custom functions.
- **Implement Error Handling:** Agents can and will make mistakes. Implement robust error handling and recovery mechanisms to ensure that your agents can handle unexpected situations.
- **Monitor and Evaluate:** Continuously monitor and evaluate the performance of your agents. This will help you to identify areas for improvement and refine your agent's design.
- **Human-in-the-Loop:** For critical tasks, consider incorporating a human-in-the-loop to provide oversight and guidance. This can help to prevent errors and ensure that the agent's actions are aligned with your goals.

## Examples

### Example 1: Building a Research Assistant with LangChain and DuckDuckGo

This example demonstrates how to build a research assistant that uses DuckDuckGo for web searches.

```python
from langchain_community.tools import DuckDuckGoSearchRun
from langchain.agents import initialize_agent, AgentType
from langchain_openai import OpenAI

# Initialize the LLM
llm = OpenAI(temperature=0)

# Initialize the search tool
search = DuckDuckGoSearchRun()

# Create a list of tools
tools = [
    {
        "name": "search",
        "func": search.run,
        "description": "Useful for when you need to answer questions about current events."
    }
]

# Initialize the agent
agent = initialize_agent(
    tools,
    llm,
    agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
    verbose=True
)

# Run the agent
agent.run("What are the latest advancements in generative AI?")
```

### Example 2: Creating a Financial Analyst Crew with CrewAI

This example showcases a more complex multi-agent system for financial analysis using CrewAI.

```python
from crewai import Agent, Task, Crew, Process
from langchain_community.tools import DuckDuckGoSearchRun

# Define the search tool
search_tool = DuckDuckGoSearchRun()

# Define the agents
researcher = Agent(
  role='Senior Financial Analyst',
  goal='Analyze the financial performance of Tesla Inc. (TSLA)',
  backstory=("You are a seasoned financial analyst with a knack for dissecting financial statements "
             "and identifying key performance indicators. You are known for your meticulous attention to detail."),
  verbose=True,
  allow_delegation=False,
  tools=[search_tool]
)

writer = Agent(
  role='Financial News Reporter',
  goal='Write a concise and informative news article on Tesla\'s financial performance',
  backstory=("You are a financial news reporter for a major publication. You have a talent for translating "
             "complex financial data into a clear and engaging narrative for a general audience."),
  verbose=True,
  allow_delegation=True
)

# Define the tasks
task1 = Task(
  description=("Analyze Tesla\'s latest quarterly financial report. "
               "Focus on revenue, net income, and earnings per share. "
               "Compare the results to the previous quarter and the same quarter last year."),
  expected_output="A detailed analysis of Tesla\'s financial performance, including key metrics and trends.",
  agent=researcher
)

task2 = Task(
  description=("Write a news article based on the financial analysis. "
               "The article should be approximately 500 words and highlight the key takeaways for investors."),
  expected_output="A well-written news article in markdown format.",
  agent=writer
)

# Create the crew
crew = Crew(
  agents=[researcher, writer],
  tasks=[task1, task2],
  process=Process.sequential
)

# Run the crew
result = crew.kickoff()

print(result)
```

### Example 3: A Template for a Generic Research Agent

This template can be used as a starting point for building your own research agents.

```python
from crewai import Agent, Task, Crew, Process
from langchain_community.tools import DuckDuckGoSearchRun

# Define the search tool
search_tool = DuckDuckGoSearchRun()

# Define the agent
research_agent = Agent(
  role='Research Specialist',
  goal='To provide accurate and well-researched information on any given topic.',
  backstory=("You are an expert researcher with access to a vast amount of information. "
             "You are skilled at finding, evaluating, and synthesizing information from various sources."),
  verbose=True,
  allow_delegation=False,
  tools=[search_tool]
)

# Define the task
research_task = Task(
  description='Research the topic: {topic}',
  expected_output='A comprehensive report on the topic, including key findings and a list of sources.',
  agent=research_agent
)

# Create the crew
research_crew = Crew(
  agents=[research_agent],
  tasks=[research_task],
  process=Process.sequential
)

# Run the crew with a specific topic
topic_to_research = "The impact of climate change on global food security"
result = research_crew.kickoff(inputs={'topic': topic_to_research})

print(result)
```
## References

1.  [Top AI Agent Frameworks in 2025: LangChain, AutoGen, CrewAI ...](https://medium.com/@iamanraghuvanshi/agentic-ai-3-top-ai-agent-frameworks-in-2025-langchain-autogen-crewai-beyond-2fc3388e7dec)
2.  [Top 7 Agentic AI Frameworks in 2026: LangChain, CrewAI, and ...](https://www.alphamatch.ai/blog/top-agentic-ai-frameworks-2026)
3.  [CrewAI vs LangChain vs AutoGPT vs LlamaIndex: - Draft'n run](https://draftnrun.com/en/blog/250915-ai-agent-frameworks-comparison/)
4.  [Introduction to LangChain: Build AI Agents with Python](https://academy.langchain.com/courses/foundation-introduction-to-langchain-python)
5.  [Quickstart - CrewAI Documentation](https://docs.crewai.com/en/quickstart)
6.  [CrewAI: A Guide With Examples of Multi AI Agent Systems - DataCamp](https://www.datacamp.com/tutorial/crew-ai)
7.  [AutoGPT on GitHub](https://github.com/Significant-Gravitas/Auto-GPT)
