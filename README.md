 # Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date:21/10/2025
# Register no:212223040181
# Aim: Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

# AI Tools Required:

# Explanation:
Experiment the persona pattern as a programmer for any specific applications related with your interesting area. 
Generate the outoput using more than one AI tool and based on the code generation analyse and discussing that. 

📝 Introduction

In modern software development, AI-assisted coding has emerged as a transformative concept.
Rather than manually constructing every function, developers can now interact with AI systems like ChatGPT or Lovable AI to:

Generate code snippets

Debug existing logic

Connect APIs and databases

Generate documentation and recommendations

However, the effectiveness of these systems depends on the quality of prompts used.
A vague prompt leads to generic, sometimes incorrect results — while a structured and context-rich prompt leads to precise, production-ready outputs.

This experiment focuses on prompt engineering as a skill that every software developer should learn.

💡 Theory: What Is Prompt Engineering?

Prompt engineering is the practice of crafting structured, context-aware inputs for AI systems to produce optimal results.
A well-designed prompt generally includes:

Element	Description	Example
Role	Defines the AI’s persona	“You are a senior Python developer.”
Task	Specifies the goal	“Write code to fetch and compare weather data from two APIs.”
Input Data	Provides real-world context	“City name, API key, API URLs.”
Constraints	Adds rules and limits	“Use error handling and display results in a table.”
Output Format	Ensures clarity	“Display results as a JSON summary and human-readable insights.”

This experiment shows how a developer evolves prompts through multiple stages to achieve professional-quality AI-assisted code.

🧩 Stage 1 – Generating Python Code for Multiple APIs
🧾 Prompt 1 – Basic Prompt
Write a Python program to get weather data for a given city using an online API.

💻 AI Response (Basic Output)
import requests

city = input("Enter city name: ")
api_key = "YOUR_API_KEY"
url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
response = requests.get(url)
data = response.json()

print(data)

🧠 Explanation

Fetches raw JSON data from OpenWeather API.

Works correctly but lacks readability, structure, and error handling.

Demonstrates the outcome of a simple, unstructured prompt.

🧾 Prompt 2 – Improved Prompt (Intermediate)
You are a Python expert. Write a Python program that fetches both weather and air quality data for a given city using two different APIs. Display results neatly with clear labels and handle any potential errors.

💻 AI Response (Improved Code)
import requests

def get_weather(city):
    try:
        api_key = "YOUR_WEATHER_API_KEY"
        url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
        response = requests.get(url)
        response.raise_for_status()
        data = response.json()
        return data
    except Exception as e:
        return {"error": str(e)}

def get_air_quality(city):
    try:
        api_key = "YOUR_AIR_API_KEY"
        url = f"https://api.waqi.info/feed/{city}/?token={api_key}"
        response = requests.get(url)
        response.raise_for_status()
        data = response.json()
        return data
    except Exception as e:
        return {"error": str(e)}

city = input("Enter city name: ")
weather_data = get_weather(city)
air_data = get_air_quality(city)

print("\n--- Weather Data ---")
print(weather_data)

print("\n--- Air Quality Data ---")
print(air_data)

🔍 Observation

Adding context and expectations in the prompt improved:

Error handling

Function structure

Readable output

⚖️ Stage 2 – Comparing Outputs from Multiple APIs
🧾 Prompt 3 – Structured Comparison
Write Python code that compares weather and air quality data for the same city. Display a summary table showing temperature, humidity, and air quality index (AQI) side by side.

💻 AI Response
from tabulate import tabulate

def compare_data(weather_data, air_data):
    try:
        temp = weather_data['main']['temp']
        humidity = weather_data['main']['humidity']
        aqi = air_data['data']['aqi']

        table = [
            ["Temperature (°C)", temp],
            ["Humidity (%)", humidity],
            ["Air Quality Index", aqi]
        ]
        print(tabulate(table, headers=["Parameter", "Value"], tablefmt="fancy_grid"))
    except Exception as e:
        print("Error comparing data:", e)

compare_data(weather_data, air_data)

🧠 Output Example
╒══════════════════════╤══════════╕
│ Parameter            │ Value    │
╞══════════════════════╪══════════╡
│ Temperature (°C)     │ 33       │
│ Humidity (%)         │ 68       │
│ Air Quality Index    │ 142      │
╘══════════════════════╧══════════╛

💬 Observation

The prompt now requests structured formatting → output is visually organized.

The inclusion of keywords like “side by side” and “table” improved the AI’s formatting decisions.

📊 Stage 3 – Generating Insights from API Data
🧾 Prompt 4 – Insight Generation
Based on the comparison of weather and air quality data, provide text-based insights and daily recommendations. Include warnings when AQI is high or when humidity is uncomfortable.

💻 AI Response (Generated Insights)
Insights for Mumbai:
- Temperature: 32°C
- Humidity: 75%
- AQI: 154 (Unhealthy for sensitive groups)

Recommendations:
• Avoid outdoor physical activities during peak hours.
• Stay hydrated to counter high humidity.
• If you have asthma, carry a mask when outdoors.
• Prefer indoor exercise during afternoon hours.

🧠 Explanation

This advanced prompt transforms AI into an analytical assistant.
By specifying “text-based insights” and “recommendations,” the model provides real-world contextual output.

🧮 Stage 4 – Visualization and File Export
🧾 Prompt 5 – Data Visualization
Extend the existing program to visualize temperature and AQI data using matplotlib. Save the chart as 'weather_aqi_chart.png'.

💻 AI Response
import matplotlib.pyplot as plt

def visualize_data(weather_data, air_data):
    parameters = ['Temperature (°C)', 'Humidity (%)', 'AQI']
    values = [
        weather_data['main']['temp'],
        weather_data['main']['humidity'],
        air_data['data']['aqi']
    ]

    plt.bar(parameters, values, color=['skyblue', 'orange', 'lightgreen'])
    plt.title("Weather & Air Quality Comparison")
    plt.xlabel("Parameter")
    plt.ylabel("Value")
    plt.savefig("weather_aqi_chart.png")
    plt.show()

visualize_data(weather_data, air_data)

📈 Output

A bar chart showing Temperature, Humidity, and AQI.

Image file exported successfully for inclusion in reports.

📂 Stage 5 – Storing and Comparing Multiple Cities
🧾 Prompt 6 – Multi-City API Comparison
Write Python code to fetch weather and air quality data for multiple cities, store results in a CSV file, and display which city has the cleanest air.

💻 AI Response
import csv

cities = ["Delhi", "Mumbai", "Chennai", "Bangalore"]

with open("city_comparison.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerow(["City", "Temperature (°C)", "Humidity (%)", "AQI"])

    cleanest_city = None
    lowest_aqi = float('inf')

    for city in cities:
        weather = get_weather(city)
        air = get_air_quality(city)
        temp = weather['main']['temp']
        humidity = weather['main']['humidity']
        aqi = air['data']['aqi']

        writer.writerow([city, temp, humidity, aqi])

        if aqi < lowest_aqi:
            lowest_aqi = aqi
            cleanest_city = city

print(f"The city with the cleanest air is {cleanest_city} (AQI: {lowest_aqi})")

🧠 Explanation

Introduces loops, file writing, and comparative logic.

Demonstrates how a more advanced prompt enables complex program logic.

🧩 Stage 6 – Refinement with Natural Language Reporting
🧾 Prompt 7 – Report Generation
Write Python code that generates a text report summarizing weather and AQI results for each city, along with observations and recommendations. Save the report to 'daily_environment_report.txt'.

💻 AI Response
def generate_report(cities):
    with open("daily_environment_report.txt", "w") as file:
        for city in cities:
            weather = get_weather(city)
            air = get_air_quality(city)
            temp = weather['main']['temp']
            humidity = weather['main']['humidity']
            aqi = air['data']['aqi']

            file.write(f"\nCity: {city}\n")
            file.write(f"Temperature: {temp}°C\nHumidity: {humidity}%\nAQI: {aqi}\n")

            if aqi > 150:
                file.write("⚠️ Air quality is poor. Avoid outdoor activity.\n")
            else:
                file.write("✅ Air quality is good today.\n")

            file.write("-" * 40 + "\n")

generate_report(cities)

📄 Output

Creates a daily report text file summarizing multiple cities’ conditions and health suggestions.

🧾 Deliverables Summary
Stage	Description	Output Type	Learning Outcome
1	API Data Fetch	JSON Output	Basic integration
2	Data Comparison	Table	Data formatting
3	Insight Generation	Text	Analytical interpretation
4	Visualization	Graph/Image	Visual analytics
5	Multi-City Comparison	CSV	Data storage & analysis
6	Report Generation	TXT	Natural language reporting
✍️ Reflection

This exercise emphasized how prompt precision controls AI performance:

Poor prompts yield vague results.

Structured prompts with roles, constraints, and context lead to powerful code.

Iterative refinement improves not only AI understanding but also developer thinking.

Example insight:
When I added “compare outputs” to the prompt, the AI automatically structured tabulated outputs using libraries like tabulate — showing its ability to adapt when given context.
# Conclusion:
Prompt engineering transforms AI from a text generator into a collaborative coding partner.
Through this experiment, it is evident that:

Specific and contextual prompts yield better program logic.

Structured output requests enhance readability.

AI can support coding, comparison, and insight generation when guided properly.

Thus, the experiment “Framing Prompts for AI-Assisted Project Coding” successfully demonstrates the evolution of effective prompts and their impact on AI performance.

# Result: The corresponding Prompt is executed successfully.
