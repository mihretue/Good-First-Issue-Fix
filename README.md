Weather-Based Greeting Project 🎉
About the Project

This Python project greets users based on the time of day and displays the current weather in their city (if available). It’s designed to be interactive, multilingual, and resilient to API rate limits.

Goal

Demonstrate how to integrate weather APIs and geolocation in Python

Handle errors gracefully (rate limits, invalid API keys)

Provide a personalized greeting experience

Technology Stack

Python

requests for HTTP requests

pytz for timezone handling

Weather API (OpenWeatherMap
)

IP Geolocation API (ipapi.co
 or fallback)

Features

Greets users based on the current time (morning, afternoon, evening)

Supports multiple languages: English, Hindi, Greek, Italian

Automatically detects user location using IP (with fallback if API fails)

Displays weather information (temperature and description) for the detected city

Handles invalid timezones and languages gracefully

Fix for Good-First-Issue 🎯

Previously, the program could not fetch the user’s city and country due to a small bug in the get_location() function.

Fixes applied:

Corrected request.get() → requests.get()

Used .get() to safely access API data

Added fallback defaults if IP API fails or is rate-limited

def get_location():
    """Fetch user's location using IP API with fallback."""
    try:
        response = requests.get("https://ipapi.co/json")
        data = response.json()
        if data.get("error"):
            return "Addis Ababa", "Ethiopia"
        return data.get("city", "Addis Ababa"), data.get("country_name", "Ethiopia")
    except Exception:
        return "Addis Ababa", "Ethiopia"

Before & After
Before
Good evening, Mihretu Endeshaw!
greeting! (Location not found)

After
Good evening, Mihretu Endeshaw! 🌍
The weather in Addis Ababa, Ethiopia is 25°C, Clear sky


Works even if the IP API is rate-limited

Provides default city/country

Installation

Clone the repository:

git clone https://github.com/yourusername/weather-greeting.git


Navigate into the project:

cd weather-greeting


Install dependencies:

pip install -r requirements.txt


Create a .env file with your OpenWeatherMap API key:

Wheather_Map_Api_Key=YOUR_VALID_API_KEY


⚠️ Make sure there are no quotes or spaces around the key.

How to Run
python main.py

Contribution Guidelines

Explore issues labeled hacktoberfest or good-first-issue

Make your changes in a new branch and submit a pull request

Ensure code is clean, commented, and tested