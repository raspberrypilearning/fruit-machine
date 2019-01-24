## Challenge: Cloud Deploy

How could you use `CloudDeploy`, `APIFunction`, and `GeoLocation` to create a small web application which would allow users to see the weather dashboard for their location online? 


--- hints ---
--- hint ---

```
CloudDeploy[
 APIFunction[{}, weatherDashboard[$GeoLocationCity] &, "PNG"], 
 Permissions -> "Public"]
 ```

--- /hint ---
---/hints---