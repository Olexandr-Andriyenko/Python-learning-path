# APIs (Application Programming Interfaces)

They all are a set of commands, functions, protocols, and objects
that programmers can use to create software or interact with an external system.
<br>
<br>
Essentially, the API is an interface or rather a sort of barrier between your program and an external system.
And what you're trying to do is you're trying to use the rules that the API has
prescribed to make a request to the external system for some piece of data.
And if you have structured your request
according to all of the requirements that this external system has set out in
their API, then they will respond to you appropriately and give you the data that you want.
<br>
<br>
So if we think about some examples, Yahoo weather has a Yahoo
weather API
which you can tap into using your programs or apps and get things like 10-day
forecast, wind, atmosphere, astronomy conditions,
and Coinbase has their own API,
which lets you tap into the current live prices of various cryptocurrencies.

<br>
<br>
So for example, if you wanted to get crypto data,
you might use api.coinbase.com.
This is the location where the Coinbase data can be found.
Now, in addition to knowing the API endpoint,
you also have to make a request over the internet.
<br>
<br>
One of the simplest APIs that I like to introduce students to is the
[international space station current location API](http://open-notify.org/Open-Notify-API/ISS-Location-Now/).
<br>
<br>
I recommend installing a free Chrome browser plugin quote, JSON Viewer Awesome
and what it will do is whenever it sees JSON data being rendered in the
browser, it will display it in a nice tree structure.
<br>
<br>
Example:

```python
# Make a request to the ISS location API
import requests
# Get the data that we want from the endpoint, check the documentation from the api to get the URL
response = requests.get(url="http://api.open-notify.org/iss-now.json")
# Inside the object response we can  access to the response code(2xx = everything is fine)
# If the URL is wrong you can get the response code 404 (doesn't exist)
# Find the meaning of more codes here: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
print(response.status_code)

```

We should always you exception handling if we are working with apis!

```python
# Make a request to the ISS location API
import requests
# Get the data that we want from the endpoint, check the documentation from the api to get the URL
response = requests.get(url="http://api.open-notify.org/iss-now.json")
# Check if there are errors
response.raise_for_status()
# Check the data
data = response.json()
print(data)
iss_position = data["iss_position"]
print(iss_position)
longitude = data["iss_position"]["longitude"]
print(longitude)
latitude = iss_position["latitude"]
print(latitude)
iss_position = (longitude, latitude)
print(iss_position)
# If you like to know where the position on the earth is, you can use https://www.latlong.net/
```

## Exercise

We will build a Kanye quote machine. So every time you click on this button which has a Kanye emoji, you can see
he'll say different things. The data for this task you will get from this API endpoint https://kanye.rest/ !
<br>
<br>
Use this images for the UI:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/background.png" width="100">
<p>
 
 <p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/kanye.png" width="100">
<p>

<details>
 <summary>Solution</summary>

  ```python
  from tkinter import *
import requests

def get_quote():
    response = requests.get("https://api.kanye.rest")
    response.raise_for_status()
    data = response.json()
    quote = data["quote"]
    canvas.itemconfig(quote_text, text=quote)



window = Tk()
window.title("Kanye Says...")
window.config(padx=50, pady=50)

canvas = Canvas(width=300, height=414)
background_img = PhotoImage(file="background.png")
canvas.create_image(150, 207, image=background_img)
quote_text = canvas.create_text(150, 207, text="Kanye Quote Goes HERE", width=250, font=("Arial", 30, "bold"), fill="white")
canvas.grid(row=0, column=0)

kanye_img = PhotoImage(file="kanye.png")
kanye_button = Button(image=kanye_img, highlightthickness=0, command=get_quote)
kanye_button.grid(row=1, column=0)

window.mainloop()
  ```
</details>
 
We've seen how APIs can have endpoints and we said that's equivalent to the address of the place that you want to get some data
from, or you want to communicate with.
<br>
<br>
But APIs also have something called parameters.
And this is a way that allows you to give an input when you are making your API
request so that you can get different pieces of data back,
depending on your input.
<br>
<br>
Lets check the [sunrise and sunset](https://sunrise-sunset.org/api) API!

 ```python
 import requests
from datetime import datetime
# Get your position here: https://www.latlong.net/
MY_LAT = 50.973740
MY_LNG = 11.022430
parameters = {
    "lat": MY_LAT,
    "lng": MY_LNG,
    "formatted": 0,
}
response = requests.get("https://api.sunrise-sunset.org/json", params=parameters)
response.raise_for_status()
data = response.json()
sunrise = data["results"]["sunrise"]
sunset = data["results"]["sunset"]
time_now = datetime.now()
# Get only the hours of the sunrise and sunset time
sunrise_formatted = sunrise.split("T")[1].split(":")[0]
sunset_formatted = sunset.split("T")[1].split(":")[0]


 ```
