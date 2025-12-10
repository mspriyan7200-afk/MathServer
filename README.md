# Ex.04 Design a Website for Server Side Processing
## Date:10-12-2025

## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM:
```
math.html

<html>
<head>
    <title>Mileage Calculator</title>
    <style>
        body 
        {
            background: linear-gradient(cyan, green);
        }
        .id1 
        {
            text-align: center;
            color: red;
        }
        .box 
        {
            text-align: center;
            width: 60%;
            background-color: pink;
            border: solid 6px black;
            padding: 25px;
            margin: 40px auto;
        }
        .result 
        {
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1 class="id1"><u>Mileage Calculator</u></h1>
    <div class="box">
        <h2><u>Mileage Calculator</u></h2>
        <h3>Priyan - 25017302</h3>

        <form method="post">
            {% csrf_token %}
            <label>Distance Travelled</label>
            <br>
            <input type="number" name="distance"> km
            <br>
            <br>
            <label>Liters of Fuel  Consumed</label>
            <br>
            <input type="number" name="liters"> L
            <br>
            <br>
            <br>
            <button type="submit">Calculate</button>
            <br>
            <br>
            <label>Mileage</label>
            <br>
            <input class='result' type="number" name="Mileage" value={{miles}}>Km/L
        </form>
    </div>
</body>
</html>

views.py

from django.shortcuts import render
def fmiles(request):
    km = int(request.POST.get('distance', 0))
    l = int(request.POST.get('liters', 0))
    miles = km / l if request.method == 'POST' and l != 0 else 0
    print("kilometers =", km)
    print("liters =", l)
    print("Mileage =", miles)
    return render(request, 'mathapp/math.html', {'km': km, 'l': l, 'miles': miles})

    urls.py

    from django.urls import path
from mathapp import views

urlpatterns = [
    path('', views.fmiles, name='miles'),
]
```
## OUTPUT - SERVER SIDE:
![alt text](image-2.png)

## OUTPUT - WEBPAGE:
![alt text](image.png)

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
