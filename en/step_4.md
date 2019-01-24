## Creating a Function

Now that we have a user friendly dashboard, we can build a more general function, so that we can use any city as a location without having to change it in multiple places.
In Wolfram, we can define a function using `:=`, which stands for `SetDelayed`. 

--- task ---
Make a function called `weatherDashboard`, which has a parameter `location`.

You will need to use `CommonName[location]` to extract the name of your city for the title.

```
weatherDashboard[location_] :=
 Framed[
  Grid[{
  {Text[Style[CommonName[location], Large, Gray]], SpanFromLeft},
  {Show[IconData["AirTemperature", WeatherData[location, "Temperature"]], ImageSize -> 150],
  Show[IconData["WindDirection", WeatherData[location, "WindDirection"]], ImageSize -> 170]},
  {Show[IconData["RelativeHumidity", WeatherData[location, "Humidity"]], ImageSize -> 150],
  Show[IconData["WindSpeed", WeatherData[location, "WindSpeed"]], ImageSize -> 170]}
  }],
  RoundingRadius -> 40, FrameMargins -> 20, FrameStyle -> {Thick, Gray}]
  ```

--- /task ---
  
Now we can run weatherDashboard with any city simply by evaluating both the function above, and then calling the function with a specific location. You will need to use the Freeform Entry box as described in the "Exploring Weather Data" step.


![Final Interface](images/Cairo.png)
  
--- task ---
Call the weatherDashboard function with a few different cities.

Use `$GeoLocationCity` to use the location of your own computer as the city.
  
```
weatherDashboard[$GeoLocationCity]
```
--- /task ---