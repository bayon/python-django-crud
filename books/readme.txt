Django Python Crud

1) Start New Project
once python and pi installed
pip install Django
django-admin startproject projext_x
cd project_x

2) Create New App
python3 manage.py startapp books
go to .../settings.py  and add app to INSTALLED_APPS object.
create a model
    - import django.db import models
    - django.urls import reverse

    <create the model an example >

python3 manage.py makemigrations
python3 manage.py migrate

3) Admin Interface
    from django.contrib import admin
    from books.models import books

    admin.site.register(Book)

4) Views( are like controllers)

5) Urls ( routing )
    from django.urls import path
    from .import Views

    urlpatterns = [
        path('',views.Booklist.as_view(), name='book_list'),
        path('view/<int:pk>', views.BookView.as_view(), name='book_view'),
        .... new, view, edit, delete...
    ]
    

    Parent URL:
    from django.urls import include
     urlpatterns = [
         :
         path('books/', include('books.urls')),
         :
     ]

6) Run Server
python3 manage.py runserver


7) Admin Access
python3 manage.py createsuperuser


8) Templates 
{% for book in books %}
    <p>{{ book.name }}</p>
    <a href = "{% url "book_view" book.id %}" >view</a> 
{% endfor%}

    - Form 
    <form method="POST" >
        {% csrf_token %}
        {{ form.as_p }}
        <input type="submit" value="submit" />
    </form>
//===========================
IMPORTS: 
from django.db import models

from django.urls import path, include, reverse , reverse_lazy
 

from django.contrib import admin 
from books.models import admin
from books.models import Book 
from django.http import HttpResponse 
from django.views.generic import ListView, DetailView
from django.views.generic.edit import CreateView, UpdateView, DeleteView 

from . import views 
 

FUNCTIONAL IMPORTS: 
from django.shortcuts import render, redirect, get_object_or_404 
from django.forms import ModelForm 
from django.urls import path 

