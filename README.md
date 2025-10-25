 # Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date:21/10/2025
# Register no:212223040181
# Aim: Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

# AI Tools Required:

# Explanation:
Experiment the persona pattern as a programmer for any specific applications related with your interesting area. 
Generate the outoput using more than one AI tool and based on the code generation analyse and discussing that. 

💡 Introduction

Artificial Intelligence has revolutionized the way programmers design, test, and analyze software.
Modern AI systems can:

Auto-generate working code,

Integrate with APIs,

Compare data sources, and

Suggest improvements.

However, the accuracy of these AI-generated solutions depends on the prompt quality.
A vague prompt can lead to incomplete or incorrect results, whereas a structured, role-defined prompt produces precise, actionable output.

This project demonstrates how different levels of prompt design affect AI-assisted coding outcomes.

🧩 Theory of Prompt Engineering

Prompt engineering is the process of structuring text inputs that direct AI behavior.

Prompt Level	Description	Example
Basic	Simple task instruction	“Write Python code to fetch API data.”
Intermediate	Adds context or constraints	“Write Python code with error handling and formatted output.”
Advanced	Includes role, output format, and reasoning	“As a senior Python developer, write optimized, well-commented code that compares API results and prints insights in tabular format.”
Key Elements of a Good Prompt:

Role definition – “You are a data analyst…”

Task clarity – What exactly the AI should do.

Constraints – Time limit, coding style, libraries allowed.

Output expectation – Table, code, explanation, graph, etc.

Refinement loop – Adjust prompt until response fits need.

⚙️ Experimental Setup

Language: Python 3.10+

APIs Used:

OpenWeatherMap API
 (for temperature & humidity)

AQICN API
 (for air quality index)

Libraries:
requests, tabulate, matplotlib, pandas, json

Environment: Jupyter Notebook / VS Code / Google Colab

AI Tool: ChatGPT / Lovable AI

🧾 Stage-1 : API Data Fetching
🧠 Prompt
You are an expert Python developer. Write Python code that connects to two APIs: 
one providing weather data and another providing air quality data. 
Fetch results for a user-entered city, handle errors, and display the raw output.

💻 AI-Generated Code
import requests

def get_weather(city):
    try:
        api_key = "YOUR_WEATHER_API_KEY"
        url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
        response = requests.get(url)
        response.raise_for_status()
        return response.json()
    except Exception as e:
        print("Error fetching weather data:", e)
        return None

def get_air_quality(city):
    try:
        api_key = "YOUR_AIRQUALITY_API_KEY"
        url = f"https://api.waqi.info/feed/{city}/?token={api_key}"
        response = requests.get(url)
        response.raise_for_status()
        return response.json()
    except Exception as e:
        print("Error fetching air quality data:", e)
        return None

city = input("Enter city name: ")
weather_data = get_weather(city)
air_data = get_air_quality(city)

print("\n--- Weather Data ---")
print(weather_data)
print("\n--- Air Quality Data ---")
print(air_data)

🧩 Explanation

Uses requests library to access APIs.

Implements error handling with try-except.

Displays raw JSON output for both sources.

⚖️ Stage-2 : Comparing Outputs
🧠 Prompt
Write a Python script that compares temperature and humidity from the weather API 
with the air quality index (AQI) from the air quality API. 
Display results neatly using the tabulate library.

💻 AI-Generated Code
from tabulate import tabulate

def compare_results(weather, air):
    if not weather or not air:
        print("Invalid data received.")
        return

    try:
        temp = weather['main']['temp']
        humidity = weather['main']['humidity']
        aqi = air['data']['aqi']
        table = [
            ["Temperature (°C)", temp],
            ["Humidity (%)", humidity],
            ["Air Quality Index", aqi]
        ]
        print(tabulate(table, headers=["Parameter", "Value"], tablefmt="fancy_grid"))
    except KeyError:
        print("Data format mismatch. Please check API keys or responses.")

compare_results(weather_data, air_data)

🧩 Explanation

This code parses JSON objects from both APIs, extracts relevant fields, and presents them in a table.
It also checks for missing keys and mismatched formats, ensuring robustness.

🔍 Stage-3 : Insight Generation
🧠 Prompt
Analyze the compared API data and generate human-friendly insights. 
Based on AQI and temperature, provide suggestions for health and daily planning. 
Output should include reasons for each suggestion.

💻 AI-Generated Output
Insights for Bengaluru:
- Temperature: 28°C, Humidity: 61%, AQI: 90 (Moderate)
- Suggestion: Outdoor activities are safe in the morning and evening.
- Maintain hydration as humidity is moderate.
- AQI indicates fair air; mask not necessary unless allergic.

🧩 Explanation

The AI interprets the numerical data contextually to produce actionable recommendations.
Such natural-language responses can be integrated into chatbots or health apps.

🧠 Stage-4 : Prompt Refinement

To improve AI output quality, prompts were refined step-by-step.

Initial Prompt

“Compare two API outputs.”

✅ Result: Too generic → AI returned simple dictionary comparison.

Refined Prompt

“Compare temperature and humidity from weather API with AQI from air quality API. Show results in tabular format.”

✅ Result: Better, but lacked insights.

Final Prompt

“As an experienced data analyst, write Python code to fetch data from weather and air quality APIs, compare temperature, humidity, and AQI, then provide insights on health recommendations and outdoor suitability with explanations.”

✅ Result: Structured table, logical insights, clear explanations.

📊 Stage-5 : Visualization and Analysis
🧠 Prompt
Using matplotlib, visualize the temperature, humidity, and AQI values for three different cities.
Display a bar chart comparing these parameters side-by-side.

💻 AI-Generated Code
import matplotlib.pyplot as plt
import numpy as np

cities = ["Delhi", "Chennai", "Mumbai"]
temps = [35, 33, 30]
humidity = [40, 70, 65]
aqi = [180, 120, 95]

x = np.arange(len(cities))
width = 0.25

plt.bar(x - width, temps, width, label='Temperature (°C)')
plt.bar(x, humidity, width, label='Humidity (%)')
plt.bar(x + width, aqi, width, label='AQI')

plt.xlabel("Cities")
plt.ylabel("Values")
plt.title("Weather vs Air Quality Comparison")
plt.xticks(x, cities)
plt.legend()
plt.show()

🧩 Explanation

This visualization allows users to see correlations between heat, humidity, and air quality.
For instance, higher humidity may coincide with lower AQI due to moisture settling dust.

📦 Deliverables
Stage	Description	Output
1	Python Code for Multiple APIs	Raw JSON Data
2	Comparison Script	Tabular Output
3	Insight Generation	Textual Recommendations
4	Prompt Refinement	Structured, AI-enhanced Responses
5	Visualization	Graphical Output
🧩 Advanced Example – Combining APIs and Insights

A more advanced prompt version can integrate multiple steps:

🧠 Prompt
Create a Python program that:
1. Fetches data from both weather and air quality APIs for five cities.
2. Stores them in a pandas DataFrame.
3. Displays results in tabular and graphical forms.
4. Provides a short AI-generated paragraph summarizing city-wise health insights.

💻 AI-Generated Code (Excerpt)
import pandas as pd
import matplotlib.pyplot as plt

data = {
    "City": ["Delhi", "Chennai", "Mumbai", "Bangalore", "Kolkata"],
    "Temperature": [35, 33, 30, 28, 31],
    "Humidity": [40, 70, 65, 61, 68],
    "AQI": [180, 120, 95, 90, 130]
}

df = pd.DataFrame(data)
print(df)

df.plot(x="City", y=["Temperature", "Humidity", "AQI"], kind="bar", figsize=(8,5))
plt.title("City-wise Environmental Analysis")
plt.ylabel("Values")
plt.show()

print("\nAI-Generated Insights:")
for i, row in df.iterrows():
    if row.AQI > 150:
        print(f"{row.City}: High pollution – avoid outdoor exercise.")
    elif row.AQI > 100:
        print(f"{row.City}: Moderate AQI – stay hydrated and limit outdoor time.")
    else:
        print(f"{row.City}: Air is clean – outdoor activities are safe.")

✍️ Reflection

This project demonstrated that AI’s intelligence depends heavily on human input precision.
Poor prompts caused incomplete data or irrelevant code, while specific, role-oriented prompts produced reliable and structured outputs.
Each refinement cycle taught:

Clarity = Quality

Constraints = Consistency

Context = Correctness

In future work, prompts can be expanded for:

Automated visualization generation

API error recovery

Multi-parameter correlation (e.g., rainfall vs. AQI trends)
# Conclusion:
Prompt engineering transforms AI from a text generator into a collaborative coding partner.
Through this experiment, it is evident that:

Specific and contextual prompts yield better program logic.

Structured output requests enhance readability.

AI can support coding, comparison, and insight generation when guided properly.

Thus, the experiment “Framing Prompts for AI-Assisted Project Coding” successfully demonstrates the evolution of effective prompts and their impact on AI performance.

# Result: The corresponding Prompt is executed successfully.
