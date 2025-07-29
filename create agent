from langgraph.prebuilt import create_react_agent
from langchain_google_genai import ChatGoogleGenerativeAI
from langchain.tools.shell.tool import ShellTool  

llm = ChatGoogleGenerativeAI(
    model="gemini-2.0-flash",
    google_api_key="AIzaSyBooWQhuxQJOzJWA5JGKF_SQceLi9mGczM",
    convert_system_message_to_human=True,
    temperature=0.7
)

shell_tool = ShellTool()
tools = [shell_tool]

# 3. Create the agent using Gemini model
agent = create_react_agent(llm, tools)

# 4. Input message
input_message = {
    "role": "user",
    "content": (
        "Download the README here and identify the link for LangChain tutorials: "
        "https://raw.githubusercontent.com/langchain-ai/langchain/master/README.md"
    ),
}

# 5. Stream response
for step in agent.stream(
    {"messages": [input_message]},
    stream_mode="values",
):
    step["messages"][-1].pretty_print()
