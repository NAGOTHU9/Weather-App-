# Weather-App-
import requests

api_key = '30d4741c779ba94c470ca1f63045390a'

user_input = input("Enter city: ")

weather_data = requests.get(
    f"https://api.openweathermap.org/data/2.5/weather?q={user_input}&units=imperial&APPID={api_key}")

if weather_data.json()['cod'] == '404':
    print("No City Found")
else:
    weather = weather_data.json()['weather'][0]['main']
    temp = weather_data.json()['main']['temp']
    humidity =  weather_data.json()['main']['humidity']
    condition =  weather_data.json()["weather"][0]["description"].title()
   
    temp_celsius = round((temp - 32) * 5 / 9)
    print(f"The weather in {user_input} is: {weather}")
    print(f"The temperature in {user_input} is: {temp_celsius}ºC")
    print(f"The humidity in {user_input} is: {humidity}%")
    print(f"The condition in {user_input} is: {condition}")
