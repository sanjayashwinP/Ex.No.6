 # Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date:21/10/2025
# Register no:212223040181
# Aim: Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

# AI Tools Required:

# Explanation:
Experiment the persona pattern as a programmer for any specific applications related with your interesting area. 
Generate the outoput using more than one AI tool and based on the code generation analyse and discussing that. 

Objective

To learn how to design effective prompts for AI tools (like ChatGPT or Lovable AI) that assist in coding tasks for mini or final-year projects.
Learners will explore how prompt clarity and refinement improve AI-generated code, comparisons, and insights.

🎯 Aim

To develop structured prompts that guide AI in:

Generating Python code to interact with multiple APIs

Comparing results from those APIs

Suggesting meaningful insights or next-step recommendations

📝 Introduction

Artificial Intelligence (AI) tools can automate coding tasks when guided through precise prompt engineering.
Instead of manually writing every line, developers can communicate with AI systems using well-crafted prompts to:

Retrieve data from different APIs

Compare and analyze results

Produce data-driven insights

This README demonstrates how a simple prompt can evolve into an advanced one, improving both accuracy and usefulness.

💡 Theory of Prompt Engineering

Prompt engineering is the method of crafting effective queries or instructions for AI.
A good prompt defines:

Role: sets context for the AI (e.g., “You are an expert Python developer.”)

Task: specifies the goal or problem to solve

Constraints: defines conditions like output type or format

Expected Output: directs structure (e.g., “display in table format”)

The clearer the prompt, the better and more accurate the AI output.

🧩 Stage 1 – Generate Python Code for Multiple APIs
🧾 Prompt
You are an expert Python developer. Write a Python program to fetch data from two different APIs — one providing weather data and another providing air quality data — for a given city. The code should handle errors and display both results clearly.

💻 AI-Generated Code
import requests

def get_weather(city):
    try:
        api_key = "YOUR_WEATHER_API_KEY"
        url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
        response = requests.get(url)
        return response.json()
    except Exception as e:
        return {"error": str(e)}

def get_air_quality(city):
    try:
        api_key = "YOUR_AIRQUALITY_API_KEY"
        url = f"https://api.waqi.info/feed/{city}/?token={api_key}"
        response = requests.get(url)
        return response.json()
    except Exception as e:
        return {"error": str(e)}

city = input("Enter city name: ")
weather = get_weather(city)
air_quality = get_air_quality(city)

print("\n--- Weather Data ---")
print(weather)
print("\n--- Air Quality Data ---")
print(air_quality)

🧠 Explanation

This program retrieves and prints weather and air-quality data for a given city using two separate APIs.
Exception handling ensures stability in case of API or network errors.

⚖️ Stage 2 – Compare Outputs from Different APIs
🧾 Prompt
Write Python code that compares weather data (temperature, humidity) and air quality data (AQI) fetched from two APIs. Display the comparison in a neat tabular format.

💻 AI-Generated Code
from tabulate import tabulate

def compare_data(weather, air_quality):
    temp = weather['main']['temp']
    humidity = weather['main']['humidity']
    aqi = air_quality['data']['aqi']

    table = [
        ["Temperature (°C)", temp],
        ["Humidity (%)", humidity],
        ["Air Quality Index", aqi]
    ]

    print("\n--- Comparison Table ---")
    print(tabulate(table, headers=["Parameter", "Value"], tablefmt="fancy_grid"))

compare_data(weather, air_quality)

🧠 Explanation

The code compares selected metrics from both APIs and presents them using the tabulate library.
This visualization helps identify environmental correlations quickly.

🔍 Stage 3 – Generate Insights and Next Steps
🧾 Prompt
Based on the comparison of weather and air quality data, provide insights or suggestions for daily planning. For example, when air quality is poor or humidity is high, what should users do? Write AI-generated text recommendations.

🧠 AI-Generated Insights
Insights for Chennai:
- Current temperature: 33°C, Humidity: 70%, AQI: 142 (Moderate pollution)
- Suggestion: Avoid outdoor exercise during afternoon hours.
- Keep hydrated due to high humidity.
- If you have respiratory issues, wear a mask outdoors.
- Schedule outdoor activities early in the morning for better air quality.

💬 Explanation

The AI converts raw data into real-world recommendations, demonstrating how prompt engineering enables meaningful data interpretation.

📦 Deliverables Summary
Stage	Description	Deliverable	Output Type
1	API Integration	Python code to fetch weather & air quality data	JSON Output
2	Output Comparison	Tabulated comparison program	Table
3	Insights	AI-generated recommendations	Text
✍️ Reflection Note

This activity improved my understanding of prompt-based coding.
Initially, my simple prompts produced generic results. Refining them with more context, role definitions, and output expectations led to cleaner, more usable code.
The key lesson is that prompt clarity equals code quality.
Future improvements could include adding visualization (graphs) and multi-API aggregation for broader analysis.
# Conclusion:
Prompt engineering transforms AI from a text generator into a collaborative coding partner.
Through this experiment, it is evident that:

Specific and contextual prompts yield better program logic.

Structured output requests enhance readability.

AI can support coding, comparison, and insight generation when guided properly.

Thus, the experiment “Framing Prompts for AI-Assisted Project Coding” successfully demonstrates the evolution of effective prompts and their impact on AI performance.

# Result: The corresponding Prompt is executed successfully.
