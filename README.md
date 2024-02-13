# Python-and-Django-Task

## Creating Virtual Environment
When developing this Django project, I have used a Python virtual environment. This helps me in maintaining consistency and prevents potential conflicts between different projects. Here's how I have set up and activate a virtual environment for my Django project:
```
   1. Install Virtualenv: I have installed the virtualenv via pip:
           [pip install virtualenv]
   2. Create a Virtual Environment: In my project directory in the terminal and I have run the following command to create a virtual environment named env:
           [virtualenv env]
   3. Activate the Virtual Environment: As I used Ubuntu 22.04 operating system, the activation command in this case is :
           [source env/bin/activate]
   4. Install Django and Other Dependencies: While the virtual environment is active, I have installed Django and other dependencies for my project using pip:
           [pip install django]
```
By using a virtual environment, It is ensured that my project dependencies are managed separately from other projects and from the system Python installation, providing a clean and isolated environment for your development work.

## Creating Web App Using Django
To build a basic web app with Python and Django and display a table visualization of the provided JSON data on the home page, I have followed these steps:
orderedList.marker
```
    1. Set up and create Django Project: I have created a Django project using VSCode IDE.
    2. Load JSON Data: I have load the JSON data directly in the view function.
    3. Create Views: I have written a view function to handle the rendering of the home page and passing the JSON data to the template.
    4. Create Templates: I have designed an HTML template to render the table visualization. Iterate through the JSON data to display it in a table format.
```
Here's a basic example of how I have implement the above steps:
```
    1. Create a new Django project:
       django-admin startproject myproject
    2. Create a new Django app:
       python manage.py startapp myapp
    3. In my views.py file in the myapp directory, I have defined a view function to load the JSON data and render the home page:
       from django.shortcuts import render
       import json
       
       def home(request):
           with open('./data.json') as f:  ## provide the full directory.
               data = json.load(f)
           return render(request, 'home.html', {'data': data})
    4. Create a templates directory inside the myapp directory and within it, I created a new HTML file named home.html. Inside home.html, I have rendered the JSON data in a table format:
       <!DOCTYPE html>
       <html lang="en">
       <head>
           <meta charset="UTF-8">
           <meta name="viewport" content="width=device-width, initial-scale=1.0">
           <title>Table Visualization</title>
       </head>
       <body>
           <table border="1">
               <thead>
                   <tr>
                       <th>Date</th>
                       <th>Trade Code</th>
                       <th>High</th>
                       <th>Low</th>
                       <th>Open</th>
                       <th>Close</th>
                       <th>Volume</th>
                   </tr>
               </thead>
               <tbody>
                   {% for item in data %}
                   <tr>
                       <td>{{ item.date }}</td>
                       <td>{{ item.trade_code }}</td>
                       <td>{{ item.high }}</td>
                       <td>{{ item.low }}</td>
                       <td>{{ item.open }}</td>
                       <td>{{ item.close }}</td>
                       <td>{{ item.volume }}</td>
                   </tr>
                   {% endfor %}
               </tbody>
           </table>
       </body>
       </html>
    5. I updated urls.py in the myproject/myproject/ directory to include a URL pattern for the home page:
       from django.urls import path
       from myapp.views import home
       
       urlpatterns = [
           path('', home, name='home'),
       ]
    6. Run the Django development server:
       python manage.py runserver
```
Now, if you visit http://127.0.0.1:8001/ in your web browser, you should see a table visualization of the JSON data on the home page.
