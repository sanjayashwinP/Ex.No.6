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

🧩 Section 1 – Concept of Prompt Engineering
🧠 Definition

Prompt engineering is the technique of formulating clear, structured inputs that instruct an AI system to produce desired outputs.

🧩 Components of a Good Prompt
Element	Description	Example
Role	Defines who the AI should act as	“You are a Python developer.”
Context	Sets background for the task	“We are building a city environment analysis tool.”
Task	Specifies exact goal	“Write Python code to fetch data from APIs.”
Constraints	Adds rules	“Include error handling and visualization.”
Expected Output	Defines format	“Output results as a table and chart.”
🧩 Section 2 – Stage 1: Simple Prompt → Single API Integration
🧾 Prompt 1.1
Write Python code to fetch current temperature and humidity for a given city using OpenWeather API.

💻 AI-Generated Code
import requests

city = input("Enter city name: ")
api_key = "YOUR_API_KEY"
url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
response = requests.get(url)
data = response.json()

print("City:", data['name'])
print("Temperature:", data['main']['temp'], "°C")
print("Humidity:", data['main']['humidity'], "%")

📈 Sample Output
City: Chennai
Temperature: 31 °C
Humidity: 72 %

🧠 Analysis

The output is functional but lacks exception handling or data formatting.

Demonstrates how a minimal prompt yields a basic working script.

🧩 Section 3 – Stage 2: Intermediate Prompt → Multi-API Integration
🧾 Prompt 2.1
You are a Python developer. Create a program that fetches weather data (temperature, humidity) and air quality data (AQI) for a given city using two APIs. Display both results in a structured format.

💻 AI-Generated Code
import requests

def get_weather(city):
    key = "YOUR_WEATHER_API_KEY"
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={key}&units=metric"
    return requests.get(url).json()

def get_air(city):
    key = "YOUR_AQI_API_KEY"
    url = f"https://api.waqi.info/feed/{city}/?token={key}"
    return requests.get(url).json()

city = input("Enter city name: ")
w = get_weather(city)
a = get_air(city)

print("\n--- Weather Data ---")
print(f"Temperature: {w['main']['temp']}°C")
print(f"Humidity: {w['main']['humidity']}%")

print("\n--- Air Quality Data ---")
print(f"AQI: {a['data']['aqi']}")

📊 Sample Output
--- Weather Data ---
Temperature: 30°C
Humidity: 70%

--- Air Quality Data ---
AQI: 148

🧠 Discussion

The addition of a second API increases the complexity.
The AI now understands the need for two functions, input reuse, and structured printing.

🧩 Section 4 – Stage 3: Adding Error Handling & Modular Design
🧾 Prompt 3.1
Enhance the previous program with proper error handling. If an API fails, display an error message instead of crashing. Use functions for clarity.

💻 AI-Generated Code
import requests

def safe_request(url):
    try:
        r = requests.get(url, timeout=10)
        r.raise_for_status()
        return r.json()
    except Exception as e:
        return {"error": str(e)}

def get_weather(city):
    key = "YOUR_WEATHER_API_KEY"
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={key}&units=metric"
    return safe_request(url)

def get_air(city):
    key = "YOUR_AQI_API_KEY"
    url = f"https://api.waqi.info/feed/{city}/?token={key}"
    return safe_request(url)

city = input("Enter city name: ")
weather = get_weather(city)
air = get_air(city)

if "error" in weather:
    print("Weather API Error:", weather["error"])
else:
    print("Temperature:", weather['main']['temp'])

if "error" in air:
    print("Air API Error:", air["error"])
else:
    print("AQI:", air['data']['aqi'])

✅ Improvement

Adds structured exception handling

Uses modular safe_request()

Handles connection errors gracefully

🧩 Section 5 – Stage 4: Output Comparison with Visualization
🧾 Prompt 4.1
Compare weather and air quality parameters and visualize them in a bar chart using matplotlib.

💻 AI-Generated Code
import matplotlib.pyplot as plt

def show_chart(weather, air):
    temp = weather['main']['temp']
    humidity = weather['main']['humidity']
    aqi = air['data']['aqi']

    x = ['Temperature (°C)', 'Humidity (%)', 'AQI']
    y = [temp, humidity, aqi]

    plt.bar(x, y, color=['blue', 'orange', 'green'])
    plt.title('Weather vs Air Quality')
    plt.ylabel('Value')
    plt.show()

show_chart(weather, air)

📈 Output Example

A simple bar chart visualizing Temperature, Humidity, and AQI.
Visual outputs make AI-generated code more meaningful in data analysis contexts.

🧩 Section 6 – Stage 5: Multi-City Comparison & CSV Export
🧾 Prompt 5.1
Fetch weather and air quality data for multiple cities, compare their AQI levels, and save results to a CSV file.

💻 AI-Generated Code
import csv

cities = ["Delhi", "Mumbai", "Chennai", "Bangalore"]

with open("city_data.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerow(["City", "Temperature", "Humidity", "AQI"])

    best_city = None
    best_aqi = float('inf')

    for c in cities:
        w = get_weather(c)
        a = get_air(c)
        t = w['main']['temp']
        h = w['main']['humidity']
        q = a['data']['aqi']
        writer.writerow([c, t, h, q])
        if q < best_aqi:
            best_aqi, best_city = q, c

print(f"City with best air quality: {best_city} (AQI {best_aqi})")

📂 Generated File

city_data.csv containing comparative data for multiple cities.

🧩 Section 7 – Stage 6: Insight and Report Generation
🧾 Prompt 6.1
Based on the CSV data, generate a text report highlighting which city has poor air quality and provide recommendations for citizens.

💻 AI-Generated Code
import pandas as pd

def report_from_csv(filename):
    df = pd.read_csv(filename)
    worst = df.loc[df['AQI'].idxmax()]
    best = df.loc[df['AQI'].idxmin()]

    with open("environment_report.txt", "w") as f:
        f.write(f"Best City: {best['City']} (AQI: {best['AQI']})\n")
        f.write(f"Worst City: {worst['City']} (AQI: {worst['AQI']})\n\n")
        if worst['AQI'] > 150:
            f.write(f"Recommendation for {worst['City']}: Avoid outdoor activities.\n")
        f.write("Overall Observation: AQI varies based on weather and pollution sources.\n")

report_from_csv("city_data.csv")

📘 Output File: environment_report.txt
Best City: Bangalore (AQI: 72)
Worst City: Delhi (AQI: 182)

Recommendation for Delhi: Avoid outdoor activities.
Overall Observation: AQI varies based on weather and pollution sources.

🧩 Section 8 – Stage 7: Adding API Response Validation
🧾 Prompt 7.1
Enhance the program to validate API responses and skip cities where data retrieval fails.

💻 AI-Generated Code
def safe_get_data(city):
    w = get_weather(city)
    a = get_air(city)
    if 'main' not in w or 'data' not in a:
        print(f"Skipping {city}: Invalid data.")
        return None
    return w, a

data = []
for c in cities:
    res = safe_get_data(c)
    if res:
        w, a = res
        data.append((c, w['main']['temp'], w['main']['humidity'], a['data']['aqi']))

✅ Improvement

The AI now filters out failed API responses, increasing robustness.

🧩 Section 9 – Stage 8: AI-Generated Insights in Natural Language
🧾 Prompt 8.1
Analyze the CSV data and write an AI-style commentary summarizing patterns in temperature, humidity, and air quality.

💻 AI-Generated Output
Data Summary:
- Cities with higher humidity (Chennai, Mumbai) tend to have moderate AQI.
- Delhi shows consistently poor air quality regardless of humidity.
- Bangalore maintains relatively clean air due to balanced weather and greenery.

Actionable Insight:
Urban planning should focus on reducing industrial emissions in dense regions.

🧩 Section 10 – Stage 9: Advanced Prompt – Correlation Analysis
🧾 Prompt 9.1
Write Python code to calculate correlation between humidity and AQI values using Pearson correlation and display the result.

💻 AI-Generated Code
import pandas as pd
from scipy.stats import pearsonr

df = pd.read_csv("city_data.csv")
corr, _ = pearsonr(df['Humidity'], df['AQI'])
print(f"Correlation between Humidity and AQI: {corr:.2f}")

📈 Example Output
Correlation between Humidity and AQI: -0.46

🧠 Interpretation

Negative correlation suggests that higher humidity may slightly reduce airborne pollutants.

🧩 Section 11 – Stage 10: Advanced Visualization
🧾 Prompt 10.1
Use matplotlib to draw a scatter plot between humidity and AQI values for multiple cities.

💻 AI-Generated Code
plt.scatter(df['Humidity'], df['AQI'], color='purple')
plt.title("Humidity vs AQI")
plt.xlabel("Humidity (%)")
plt.ylabel("AQI")
plt.grid(True)
plt.show()

🧠 Observation

The scatter plot visually represents correlation strength — an effective analytical extension generated by prompt refinement.

🧾 Section 12 – Deliverables Summary
Stage	Description	AI Output	Key Skill
1	Basic API Fetch	Raw JSON	Simple Prompt
2	Multi-API Fetch	Structured Text	Contextual Prompt
3	Error Handling	Modular Code	Clarity
4	Visualization	Chart	Formatting
5	Multi-City CSV	File I/O	Analytical Thinking
6	Reports	Text File	Interpretation
7	Validation	Data Filtering	Reliability
8	AI Insights	Narrative	Critical Analysis
9	Correlation	Statistical Output	Advanced Prompt
10	Visualization	Graph	Data Storytelling
✍️ Reflection

Throughout this experiment, each iteration of prompt refinement:

Produced smarter, more structured outputs.

Encouraged logical decomposition before coding.

Highlighted that AI can generate not only syntax, but also analysis and explanations.

Key learning outcomes:

A well-phrased prompt = well-structured code.

AI is a coding collaborator, not just a code generator.

Re-prompting and refining context significantly improve result quality.

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
