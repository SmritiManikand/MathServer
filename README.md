# Ex.05 Design a Website for Server Side Processing
## Date: 04.04.2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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

## PROGRAM :

### HTML FILE
```
<html>

<head>
   
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    
    <title>SURFACE AREA OF RIGHT CYLINDER</title>

    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style type="text/css">
        *{
            font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        }

        body {
            background-color: coral;
        }

        .edge {
            display: flex;
            height: 100vh;
            width: 100%;    
            justify-content: center;
            align-items: center;
        }

        .box {
            display: block;
            width: 550px;
            min-height: 300px;
            font-size: 20px;
            background-color: lightseagreen;
            border-radius: 10px;
            box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
        }

        .formelt {
            color: black;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }

        h2 {
            color: red;
            text-align: center;
            padding-top: 20px;
        }

        input {
            margin: 5px;
            padding: 5px;
            border-radius: 5px;
            border: none;
        }
    </style>
</head>

<body>
    <div class="edge">
        <div class="box">
            <h2>SMRITI M (212221040157)</h2>
            <h2>SURFACE AREA OF RIGHT CYLINDER </h2>

            <form method="POST" id="cylinderForm">
                <div class="formelt">
                    Radius : <input type="text" name="radius" id="radius"></input><br />
                </div>
                <div class="formelt">
                    Height : <input type="text" name="height" id="height"></input><br />
                </div>
                <div class="formelt">
                    <input type="button" value="Calculate" onclick="calculateSurfaceArea()"></input><br />
                </div>
                <div class="formelt" id="result">
                    Surface Area : <span id="surfaceAreaResult"></span><br />
                </div>
            </form>
        </div>
    </div>

    <script>
        function calculateSurfaceArea() {
            var radius = document.getElementById('radius').value;
            var height = document.getElementById('height').value;

            
            radius = parseFloat(radius);
            height = parseFloat(height);

            
            var surfaceArea = 2 * Math.PI * radius * height + 2 * Math.PI * radius * radius;

            
            document.getElementById('surfaceAreaResult').textContent = surfaceArea.toFixed(2);
        }
    </script>
</body>

</html>
```
### urls.py

```
from django.contrib import admin
from django.urls import path
from webprocess import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('surface_area/', views.surface_area, name="surface_area"),  # Corrected function name
    path('', views.surface_area, name="surface_area_root"),  # Redirect to surface_area view
]
```
### view.py

```
from django.shortcuts import render
import math

def surface_area(request):
    context = {}
    context['area'] = "0"
    context['radius'] = "0"
    context['height'] = "0"
    
    if request.method == 'POST':
        print("POST method is used")
        radius = request.POST.get('radius', '0')
        height = request.POST.get('height', '0')
        
        radius = float(radius)
        height = float(height)
        print('request=', request)
        print('Radius=', radius)
        print('Height=', height)
        
        surface_area = 2 * math.pi * radius * height + 2 * math.pi * radius ** 2
        
        context['area'] = str(surface_area) 
        context['radius'] = str(radius)  
        context['height'] = str(height)  
        print('Area=', surface_area)
    return render(request, 'webprocess/project.html', context)
```

## SERVER SIDE PROCESSING:

<img width="959" alt="s2" src="https://github.com/SmritiManikand/MathServer/assets/113674204/bd05ed9f-145f-449f-a037-ee53c4c00563">


## HOMEPAGE:

<img width="958" alt="s1" src="https://github.com/SmritiManikand/MathServer/assets/113674204/c76492a5-9575-4c25-b6c9-12d53504ee80">


## RESULT:
The program for performing server side processing is completed successfully.
