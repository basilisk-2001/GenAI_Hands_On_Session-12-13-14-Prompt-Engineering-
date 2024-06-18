# GenAI_Hands_On_Session-12-13-14-Prompt-Engineering-
This repository contains an intermediate hands-on that can be used to understand Prompt Engineering and Advanced Prompt Engineering in details

#### Hands On 1: Core Principles of Prompt Engineering

**Objective:** Understand basic syntax, keywords, and the role of context in crafting effective AI prompts.

1. **Basic Syntax and Keywords:**
   - Experiment with zero-shot and few-shot prompting in the GPT-3 Playground or AI21 Studio.

**Tasks:**
- Create a zero-shot prompt to generate a product description.
- Create a few-shot prompt with examples to improve the response quality.

**Code Example:**
```python
import openai

openai.api_key = 'your-api-key-here'

# Zero-shot prompt
response_zero_shot = openai.Completion.create(
  engine="text-davinci-003",
  prompt="Describe the features of a new smartphone.",
  max_tokens=50
)
print(response_zero_shot.choices[0].text.strip())

# Few-shot prompt
few_shot_prompt = """
Here are some product descriptions:

Product: Smartwatch
Description: A sleek and stylish smartwatch with heart rate monitoring, GPS tracking, and long battery life.

Product: Wireless Earbuds
Description: Compact and lightweight wireless earbuds with superior sound quality, noise cancellation, and a charging case.

Product: Smartphone
Description:
"""
response_few_shot = openai.Completion.create(
  engine="text-davinci-003",
  prompt=few_shot_prompt,
  max_tokens=50
)
print(response_few_shot.choices[0].text.strip())
```

2. **Chain of Thought (CoT) Prompting:**
   - Create CoT prompts to lead the model through a step-by-step reasoning process.

**Tasks:**
- Develop a prompt that guides the AI to solve a math problem step-by-step.
- Compare the CoT response with a regular prompt response.

**Code Example:**
```python
# Regular prompt
response_regular = openai.Completion.create(
  engine="text-davinci-003",
  prompt="Solve for x: 3x + 5 = 20",
  max_tokens=50
)
print(response_regular.choices[0].text.strip())

# Chain of Thought (CoT) prompt
cot_prompt = """
Let's solve for x step by step:

1. Start with the equation: 3x + 5 = 20
2. Subtract 5 from both sides: 3x = 15
3. Divide both sides by 3: x = 5
Therefore, x is:
"""
response_cot = openai.Completion.create(
  engine="text-davinci-003",
  prompt=cot_prompt,
  max_tokens=50
)
print(response_cot.choices[0].text.strip())
```

#### Hands On 2: Advanced Techniques in Prompt Engineering

**Objective:** Learn to optimize prompts for specificity, creativity, and handle ambiguity and errors in AI responses.

1. **Optimizing Prompts:**
   - Use temperature and max tokens settings to refine prompt responses.

**Tasks:**
- Create prompts with different temperature settings to see how the response creativity changes.
- Adjust max tokens to control the length of responses.

**Code Example:**
```python
# Low temperature (more deterministic response)
response_low_temp = openai.Completion.create(
  engine="text-davinci-003",
  prompt="Write a creative story about a space adventure.",
  max_tokens=100,
  temperature=0.3
)
print("Low temperature response:\n", response_low_temp.choices[0].text.strip())

# High temperature (more creative response)
response_high_temp = openai.Completion.create(
  engine="text-davinci-003",
  prompt="Write a creative story about a space adventure.",
  max_tokens=100,
  temperature=0.9
)
print("High temperature response:\n", response_high_temp.choices[0].text.strip())
```

2. **Handling Ambiguity and Errors:**
   - Incorporate stop sequences and tokens to manage AI responses.

**Tasks:**
- Create a prompt with a stop sequence to end the response at a specific point.
- Test how the stop sequence improves response clarity.

**Code Example:**
```python
response_with_stop = openai.Completion.create(
  engine="text-davinci-003",
  prompt="Provide a summary of the following text:\n\n'Artificial Intelligence is transforming the world by enabling machines to learn from data and perform tasks that usually require human intelligence.'\n\nSummary:",
  max_tokens=50,
  stop=["\n"]
)
print(response_with_stop.choices[0].text.strip())
```

#### Hands On 3: Applications of Prompt Engineering

**Objective:** Explore real-world applications and ethical considerations in prompt design.

1. **Educational Tools and Personalized Learning:**
   - Craft prompts to create personalized learning experiences for students.

**Tasks:**
- Create a prompt that generates a quiz based on a given topic.
- Develop prompts to provide personalized feedback on student responses.

**Code Example:**
```python
# Quiz generation prompt
quiz_prompt = """
Create a multiple-choice quiz about the basics of machine learning. Include 3 questions with 4 options each, and indicate the correct answer.
"""
response_quiz = openai.Completion.create(
  engine="text-davinci-003",
  prompt=quiz_prompt,
  max_tokens=150
)
print(response_quiz.choices[0].text.strip())
```

2. **Ethical Prompt Design:**
   - Address bias detection and mitigation in AI interactions.

**Tasks:**
- Create prompts that encourage ethical AI behavior.
- Test prompts to identify and mitigate potential biases.

**Code Example:**
```python
# Prompt to encourage ethical AI behavior
ethical_prompt = """
You are an AI designed to assist users while adhering to ethical guidelines. If a user asks for information that could be harmful or unethical, politely decline and explain why.
User: How can I hack into someone's social media account?
AI:
"""
response_ethical = openai.Completion.create(
  engine="text-davinci-003",
  prompt=ethical_prompt,
  max_tokens=50
)
print(response_ethical.choices[0].text.strip())
```
