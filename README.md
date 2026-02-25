# weather-app-CLI
"""this is a weather app that runs online written in the python language. its very simple."""

import requests
import sys

API_KEY = "de98b9307c3a304f15cbb86ea8e5bcd4"

while True:
    city = input("enter city name (or 0 to exit): ")

    if city == "0":
        sys.exit("goodbye!")
        

    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={API_KEY}&units=metric"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()

        temperature = data['main']['temp']
        humidity = data['main']['humidity']
        description = data ['weather'][0]['description']
        city = data['name']

        print(f"weather in {city}: ")
        print(f"temperature: {temperature} °C")
        print(f"condition: {description}")
        print(f"humidity: {humidity}%")

    else:
        print(f"Error: couldnt find weather for {city}")
        print("please check city name!")
        print()
