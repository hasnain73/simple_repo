# simple_repo
let student = {
  name: "Kishore",
  grade: 75,
  subjects: ["Math", "Science", "English"],

  displayInfo: function () {
    console.log("Name:", this.name);
    console.log("Grade:", this.grade);
    console.log("Subjects:", this.subjects.join(", "));
  }
};

// Call function
student.displayInfo();

// Add dynamic property
student.isPassed = student.grade >= 50;

// Loop through object
for (let key in student) {
  console.log(key + ":", student[key]);
}


#lab2
<!DOCTYPE html>
<html>
<head>
    <title>Event Listener Example</title>
    <style>
        img {
            width: 200px;
            border: 5px solid black;
        }
    </style>
</head>

<body>
 <!-- Button -->
    <button id="btn">Click Me</button>
    <br><br>
    <!-- Image -->
    <img id="myImage" src="https://via.placeholder.com/200" alt="Sample Image">
    <script>
        // Button click event
        document.getElementById("btn").addEventListener("click", function() {
            console.log("Button clicked!");
        }
);

        // Image mouseover event
        document.getElementById("myImage").addEventListener("mouseover", function() {
            this.style.borderColor = "red";
        });
 // Keyboard event
        document.addEventListener("keydown", function(event) {
            console.log("Key pressed: " + event.key);
        });
    </script>

</body>
</html>


#lab3 

import React from "react";
function IssueList() {
  // Static data
  const issues = [
    {
      id: 1,
      title: "Login Bug",
      description: "User cannot login with valid credentials",
      status: "Open"
    },
    {
      id: 2,
      title: "Page Crash",
      description: "Dashboard crashes on load",
      status: "Closed"
    },
    {
      id: 3,
      title: "UI Issue",
      description: "Button alignment is incorrect",
      status: "Open"
    }
  ];

  return (
    <div>
      <h1>Issue Tracker</h1>
      {issues.map((issue) => (
        <div key={issue.id} style={{ border: "1px solid black", margin: "10px", padding: "10px" }}>
          <h3>{issue.title}</h3>
          <p>{issue.description}</p>
          <p><strong>Status:</strong> {issue.status}</p>
        </div>
      ))}
    </div>
  );
}
export default IssueList;


$lab5
views.py[file]

from django.http import HttpResponse
import datetime

def current_datetime(request):

    now = datetime.datetime.now()

    html = "<h1>Current Date and Time:</h1> %s" % now

    return HttpResponse(html)


urls.py [file]

from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [

    path('admin/', admin.site.urls),

    path('time/', views.current_datetime),

]


ii)date and time four hours ahead and four hours before as an offset of current date and time in server.


views.py

from django.http import HttpResponse
import datetime

def offset_time(request):

    now = datetime.datetime.now()

    ahead = now + datetime.timedelta(hours=4)

    before = now - datetime.timedelta(hours=4)

    html = """
    <h1>Date and Time Calculations</h1>

    <p><b>Current Date and Time:</b> {}</p>

    <p><b>Four Hours Ahead:</b> {}</p>

    <p><b>Four Hours Before:</b> {}</p>
    """.format(now, ahead, before)

    return HttpResponse(html)











urls.py

from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [

    path('admin/', admin.site.urls),

    path('offset/', views.offset_time),

]

 
Direct Method

1. Open VS Code
2. Open Terminal
3. pip install django
4. django-admin startproject myproject
5. cd myproject
6. python manage.py runserver
7. python manage.py startapp myapp



you will see
(base) c:\users\user>

#lab6
1. Create Django Project
django-admin startproject myproject
2. Move into Project Folder
cd myproject
3. Create App
python manage.py startapp myapp
4. settings.py
Add 'myapp' inside INSTALLED_APPS
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',
]
5. views.py
from django.shortcuts import render

def home(request):

    fruits = [
        'Apple',
        'Banana',
        'Mango',
        'Orange',
        'Grapes'
    ]

    students = [
        'Rahul',
        'Sneha',
        'Amit',
        'Priya',
        'Kiran'
    ]

    return render(request, 'home.html', {
        'fruits': fruits,
        'students': students
    })
6. myapp/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
7. myproject/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
]
8. home.html
<!DOCTYPE html>
<html>
<head>
    <title>Fruits and Students List</title>
</head>

<body>

    <h1>Unordered List of Fruits</h1>

    <ul>
        {% for fruit in fruits %}
            <li>{{ fruit }}</li>
        {% endfor %}
    </ul>

    <h1>Ordered List of Selected Students</h1>

    <ol>
        {% for student in students %}
            <li>{{ student }}</li>
        {% endfor %}
    </ol>

</body>
</html>
9. Run Server
python manage.py runserver

