## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:
To create an LCEL chain that accepts user inputs, processes them using a language model, and generates clear text responses for different real-world scenarios.

### DESIGN STEPS:

### STEP 1: Create Prompt
- Import the required LangChain libraries.
- Create a prompt template using two parameters: topic and audience.
- Define how the response should be generated.

### STEP 2: Initialize Model and Output Parser
- Initialize the ChatOpenAI model using gpt-4o-mini.
- Create a StrOutputParser to convert the model response into plain text.

### STEP 3: Create and Execute LCEL Chain
- Combine the prompt, model, and output parser using the pipe (|) operator.
- Pass different inputs using chain.invoke().
- Evaluate the generated responses for different real-world topics.

### PROGRAM:

~~~
%pip install -U langchain-core langchain-openai python-dotenv

import os
from getpass import getpass
from dotenv import load_dotenv
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.output_parsers import StrOutputParser
load_dotenv()
api_key = os.getenv("OPENAI_API_KEY")
if not api_key:
api_key = getpass("Enter your OpenAI API key: ")
os.environ["OPENAI_API_KEY"] = api_key
print("Libraries imported successfully!")

prompt = ChatPromptTemplate.from_template(
"Explain {topic} to {audience} in simple language "
"using one practical example."
)
print("Prompt created successfully!")

model = ChatOpenAI(
model="gpt-4o-mini",
temperature=0
)
print("Model initialized successfully!")

output_parser = StrOutputParser()
print("Output parser created successfully!")

chain = prompt | model | output_parser
print("LCEL chain created successfully!")

result = chain.invoke({
"topic": "Artificial Intelligence",
"audience": "school students"
})
print(result)

result = chain.invoke({
"topic": "Cybersecurity",
"audience": "college students"
})
print(result)

result = chain.invoke({
"topic": "Healthy Eating",
"audience": "children"
})
print(result)
~~~

### OUTPUT:

<img width="982" height="850" alt="Screenshot 2026-11-03 215526" src="https://github.com/user-attachments/assets/16404bf6-c0eb-4a8f-bed2-1ffedfbb494a" />

<img width="973" height="632" alt="Screenshot 2026-11-03 215548" src="https://github.com/user-attachments/assets/9a874a27-71ca-43c7-8d28-df8fcd011a2e" />

<img width="902" height="515" alt="Screenshot 2026-11-03 215557" src="https://github.com/user-attachments/assets/89ffb7d6-f47b-4dd9-b92c-5de27526caaa" />

<img width="942" height="537" alt="Screenshot 2026-11-03 215607" src="https://github.com/user-attachments/assets/dc588b0b-b306-4b72-a048-dbce54e92945" />

<img width="827" height="847" alt="Screenshot 2026-11-03 215624" src="https://github.com/user-attachments/assets/d3d62f0b-b050-4838-b6c5-c5cff3bef7fd" />

<img width="827" height="466" alt="Screenshot 2026-11-03 215631" src="https://github.com/user-attachments/assets/c3be9fc4-66e4-4864-b3b4-d034fef420e1" />



### RESULT:
Thus, an LCEL expression was successfully implemented using two prompt parameters and three key components to generate responses for real-world applications.
