Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

Aim: 

Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools.

Explanation:

Develop a python code that integrates multiple AI tool by interacting with their APIs.
Compare outputs from different APIs.
Analyze the response and the Output.

The aim is to understand how to request help from AI tools for tasks like writing Python code, integrating with APIs, comparing outputs, and generating actionable insights.




## AI Tools Used

1. OpenAI GPT API
2. Google Gemini API

---

## Python Code

```python
import requests
import json

# API Keys
OPENAI_API_KEY = "your_openai_api_key"
GEMINI_API_KEY = "your_gemini_api_key"

prompt = "Explain the benefits of Artificial Intelligence in education."

# ----------------------------
# OpenAI API Call
# ----------------------------
def get_openai_response(prompt):

    url = "https://api.openai.com/v1/chat/completions"

    headers = {
        "Authorization": f"Bearer {OPENAI_API_KEY}",
        "Content-Type": "application/json"
    }

    data = {
        "model": "gpt-4o-mini",
        "messages": [
            {"role": "user", "content": prompt}
        ]
    }

    response = requests.post(url,
                             headers=headers,
                             json=data)

    result = response.json()

    return result["choices"][0]["message"]["content"]


# ----------------------------
# Gemini API Call
# ----------------------------
def get_gemini_response(prompt):

    url = f"https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key={GEMINI_API_KEY}"

    payload = {
        "contents": [
            {
                "parts": [
                    {"text": prompt}
                ]
            }
        ]
    }

    response = requests.post(url,
                             headers={"Content-Type": "application/json"},
                             json=payload)

    result = response.json()

    return result["candidates"][0]["content"]["parts"][0]["text"]


# ----------------------------
# Compare Responses
# ----------------------------
def compare_responses(response1, response2):

    words1 = len(response1.split())
    words2 = len(response2.split())

    print("\n----- OpenAI Response -----\n")
    print(response1)

    print("\n----- Gemini Response -----\n")
    print(response2)

    print("\n----- Comparison -----")

    print(f"OpenAI Word Count: {words1}")
    print(f"Gemini Word Count: {words2}")

    if words1 > words2:
        print("OpenAI provided a more detailed response.")
    elif words2 > words1:
        print("Gemini provided a more detailed response.")
    else:
        print("Both responses have similar detail levels.")


# ----------------------------
# Main Program
# ----------------------------
openai_response = get_openai_response(prompt)
gemini_response = get_gemini_response(prompt)

compare_responses(openai_response, gemini_response)
```

---

## Sample Output

### Prompt

```
Explain the benefits of Artificial Intelligence in education.
```

### OpenAI Response (Summary)

```
Artificial Intelligence improves personalized learning,
automates grading, provides instant feedback,
and helps students learn at their own pace.
```

### Gemini Response (Summary)

```
AI supports adaptive learning, smart tutoring systems,
automated assessments, accessibility tools,
and educational analytics.
```

---

## Comparison Table

| Feature           | OpenAI GPT | Gemini   |
| ----------------- | ---------- | -------- |
| Accuracy          | High       | High     |
| Detail Level      | Moderate   | High     |
| Readability       | Excellent  | Good     |
| Examples          | Included   | Included |
| Educational Focus | Strong     | Strong   |

---

## Analysis

### OpenAI Response Analysis

* Easy to understand.
* Well-structured explanation.
* Suitable for beginners.
* Provides concise information.

### Gemini Response Analysis

* More detailed.
* Covers additional educational applications.
* Includes broader perspectives.
* Better for in-depth understanding.

---

## Actionable Insights Generated

1. AI can personalize learning for students.
2. Automated grading reduces teacher workload.
3. Intelligent tutoring systems improve learning outcomes.
4. Learning analytics help identify weak areas.
5. Educational institutions can use AI to increase efficiency and accessibility.

---

## Advantages of Multi-AI Integration

* Compare responses from multiple sources.
* Improve reliability of information.
* Reduce bias from a single model.
* Obtain more comprehensive insights.
* Support better decision-making.

---

## Result

A Python application was successfully designed to integrate multiple AI tools through APIs, compare their responses, analyze the outputs, and generate actionable insights. The experiment demonstrated that combining multiple AI systems can improve the quality and completeness of information obtained.
