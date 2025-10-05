# Ex.05 Design a Website for Server Side Processing
## Date:5/10/2025

## AIM:
 To design a website to calculate the body mass index (bmi) in the server side


## FORMULA:
BMI = W/H<sup>2</sup>
<br> BMI --> Body mass index
<br> W --> Weight
<br> H --> Height

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
```
bmi.html
<html>
    <head>
        <title>CALCULATE BMI </title>
    <style>
        body{
            font-family:Arial,sans-serif;
            background-color:rgba(69, 118, 167, 1);
            color:white;
            display:flex;
            justify-content: center;
            align-items: center;
            height:100vh;
            border-radius: 5%;
            background: rgba(83, 105, 203, 1);

        }
         body {
            font-family: Arial, sans-serif;
            margin: 45px;
            background-color: rgba(70, 108, 164, 1);
        }
        form {

            padding: 20px;
            border-radius: 8px;
            width: 500px;
            
        }
        input {
            margin-top: 10px;
            width: 100%;
            padding: 8px;
        }
        .input-row {
    display: flex;
    align-items: center;
    margin-top: 10px;
}

.input-row label {
    width: 120px;
    margin-right: 10px;
    color: black;
}

input[type="text"] {
    margin-top: 0;
    flex-grow: 1;
    padding: 8px;
    width: auto; /* override full width */
}
    

        h2 {
            margin-top: 20px;
        }
        .container {
            background-color: rgba(52, 185, 132, 1);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(79, 192, 132, 0.1);
            border-style: dashed;
        }
        label{
            font-size:20px;
            font-weight:20px;
            font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
            color:black;
        }
        h1{
            font-size:40px;
            font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
            margin-bottom:20px;
            color:rgba(245, 13, 13, 1);
        }
        .button{
             border-style: dashed;
                margin-top:20px;
        }
        .button h2{
            color:rgba(8, 12, 246, 1);
            font-weight: bold;
        }
        .submit-button{
            font-size:20px;
            font-weight: bold;
        }
   </style>
</head>
<body>
    <center>
    <div class="container">
        <div>
                <h1>BMI CALCULATER</h1>
                <h1>Devesh C (25011036)</h1>
    <form method="post">
        {% csrf_token %}
        <label for="height">HEIGHT [cm]:</label>
        <input type="text" id="height" name="height" required><br>

        <label for="weight">WEIGHT [kg]:</label>
        <input type="text" id="weight" name="weight" required>
        <div class="submit-button">
        <input type="submit" value="CALCULATE_BMI"></div>

           
    </form>

    {% if bmi %}
         <div class="button">
        <h2>YOUR BMI: {{ bmi }}</h2></div>
        {% if category %}
            <p>Category: {{ category }}</p>
        {% endif %}
    {% endif %}
        </div>
    </div>
    </center>
</body>
</html>

views.py


from django.shortcuts import render
def calculate_bmi(request):
    context={}
    context['bmi']="0"
    context['w']="0"
    context['h']="0"
    if(request.method=='POST'):
       w= float(request.POST.get('weight','0'))
       h=float(request.POST.get('height','0'))
       print('request=',request)
       
       print('Weight=',w)
       print('Height=',h)
       bmi=w/((h/100)**2)
       context['bmi']=bmi
       context['w']=w
       context['h']=h
       print('BMI=',bmi)
    return render(request,'myapp/bmi.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from myapp import views 

urlpatterns = [
    path('admin/', admin.site.urls),
    path('bmi/',views.calculate_bmi,name="bmi"),
    path('',views.calculate_bmi,name="bmicalculator")
]

```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot (26).png>)

## HOMEPAGE:
![alt text](<Screenshot (27).png>)

## RESULT:
The program for performing server side processing is completed successfully.
