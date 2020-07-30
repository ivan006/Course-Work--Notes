
# Setup

## Conda

- anaconda python 3.6 (https://www.anaconda.com/products/individual#windows)
- use conda prompt

## Enable python in gitbash (didnt use - )

- alias python='winpty python.exe'

## Atom packages
- autocomplete-python by autocomplete-python
- kite - recommended with autocomplete-python (dont install )
- platformio-ide-terminal by platformio ( dont install)
- atom-django by zacharytamas


## Create conda env

- C:\Users\ivan\Documents\multimedia\b-python-course
- C:/Users/ivan\Documents/multimedia/b-python-course
- conda --version
- didnt do this - access C:\Users\ivan\.bashrc add export PATH=~/anaconda3/bin:$PATH
- https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html
- access C:\Users\ivan\.bashrc add - . C:/ProgramData/Anaconda3/etc/profile.d/conda.sh
- conda create --name myEnv django
- conda create --name myEnv python=3.5
- If installation problem and ur using comodo try turning comodo auto-containment off
- conda info --envs
- activate myEnv
- deactivate myEnv
- conda install django

## Create a project

- django-admin startproject first_project
- Rough notes
  - https://www.anaconda.com/products/individual#windows
  - https://docs.conda.io/en/latest/miniconda.html
  - google: C:\Windows\System32\cmd.exe
  - google: anaconda install stuck at preparring transaction
  - https://bugzilla.redhat.com/show_bug.cgi?id=1468896
  - https://www.reddit.com/r/Python/comments/d9eynb/anaconda_install_freezes_or_does_not_complete/
  - google: initial python cmd hanging
  - https://stackoverflow.com/questions/50909361/python-hangs-after-some-time-continues-when-pressed-enter
  - google: python command not working
  - https://stackoverflow.com/questions/13596505/python-not-working-in-command-prompt
  - google: how to add to path system variables
  - https://docs.telerik.com/teststudio/features/test-runners/add-path-environment-variables
  - google: how to add to PYTHONPATH system variable
  - https://stackoverflow.com/questions/3701646/how-to-add-to-the-pythonpath-in-windows-so-it-finds-my-modules-packages
  - google: ## enable python cmd
  - - Add C:\Python27\ (or wherever you installed python) to the end of the PATH system variable
  - - Add C:\Python27\ (or wherever you installed python) to the end of the PYTHONPATH system variable
  - google: python not working in gitbash
  - https://stackoverflow.com/questions/32597209/python-not-working-in-the-command-line-of-git-bash
  - 
  - https://stackoverflow.com/questions/7374748/whats-the-difference-between-a-python-property-and-attribute
  - google: object level attribute p ython
  - https://dzone.com/articles/python-class-attributes-vs-instance-attributes
  - 
  - https://askubuntu.com/questions/908827/variable-path-issue-conda-command-not-found
  - google: .bashrc file where is it win7
  - https://stackoverflow.com/questions/44955805/why-does-anaconda-navigator-keeps-crashing-on-start-up-mac
  - google: there is an instance oof anaconda navigator already running
  - https://stackoverflow.com/questions/50079641/there-is-an-instance-of-anaconda-navigator-already-running-error
  - google: conda command not woking in gitbash
  - https://stackoverflow.com/questions/54501167/anaconda-and-git-bash-in-windows-conda-command-not-found
  - google: conda create django [WinError 87] The parameter is incorrect()
  - https://stackoverflow.com/questions/56305542/conda-forge-spacy-install-fails-error-winerror-87-the-parameter-is-incorrec
  - google: python command hanging in gitbash
  - google: conda version 'conda' is not recognized as an internal or external command, operable program or batch file.
  - https://stackoverflow.com/questions/44515769/conda-is-not-recognized-as-internal-or-external-command
  - Google: django1.11 then you will use from django.conf.urls import url and always use url for routing. If you use django 2/3 then you will use path instead of url. And it imported code is from django.urls import path


# Usage

## Components overview
- url handler - urls.py
- base function - views.py
- data handler - models
- layout handler - templates

## Run server
- Orient to 
  - C:/Users/ivan\Documents/multimedia/b-python-course/first_project
- Run
  - activate myEnv
  - python manage.py runserver
- Orient to
  - http://127.0.0.1:8000/ 

## Create an app
- python manage.py startapp first_app


## Register app
- Orient to 
  - first_project > settings.py
  - INSTALLED_APPS = [
- Add “‘first_app’”

## Views

- Add
	```
	from django.http import HttpResponse
	# Create your views here.
	def index(request):
		return HttpResponse("Hello World")
	```

## Urls using views
- Orient to 
  - first_project > urls.py
- Add “from first_app import views”
- Orient to 
  - urlpatterns = [
- Add “path('',views.index, name="index"),”

## Urls with app scope
- Orient to 
  - first_app
- Manually create a “urls.py” file 
- Add “from django.conf.urls import url”
  ```

  from django.conf.urls import url
  from first_app import views

  urlpatterns = [
      path('', views.index, name="index")
  ]
  ```

- Orient to 
  - first_project > urls.py
- Add “from django.conf.urls import include”
- Orient to 
  - urlpatterns = [
- Add “path('first_app/', include('first_app.urls')),”

## Templates
- Orient to 
  - First_project
- Add “templates” folder
- Orient to 
  - First_project
  - First_project
  - Settings.py
  - The blank line below “BASE_DIR =”
- Add “TEMPLATE_DIR = os.path.join(BASE_DIR,"templates")”
- Orient to 
  - TEMPLATES = [
  - 'DIRS': [],
- Update “'DIRS': [TEMPLATE_DIR,],”
- Orient to 
  - First_project
  - templates
- Add “first_app” folder
- Orient to 
  - first_app
- Add “index.html” file
- Orient to 
  - Index.html
- Add 
  ```
  <!DOCTYPE html>
  <html lang="en" dir="ltr">
    <head>
      <meta charset="utf-8">
      <title>First app</title>
    </head>
    <body>
      <h1>Hello this is index.html!</h1>
      {{ insert_me }}
    </body>
  </html>
  ```
- Orient to 
  - First_project
  - First_app
  - views.py
  - return HttpResponse("Hello World")
- Update
  ```
  my_dict = {'insert_me':"Hello I am from view.py!"}
  return render(request, "first_app/index.html", context=my_dict)
  ```

## Static files
### Static dir setup
- Orient to 
  - First_project
- Add “static” folder
- Orient to 
  - First_project
  - First_project
  - Settings.py
  - The blank line below “TEMPLATES = [”
- Add “STATIC_DIR = os.path.join(BASE_DIR,"templates")”
- Orient to 
  - The blank line below STATIC_URL =
- Add 
  ```
  STATICFILES_DIRS = [
      STATIC_DIR,
  ]
  ```


### Images dir
- Orient to 
  - First_project
  - static
- Add “images” folder
- Orient to 
  - images
- Add “image.png” file
- Orient to 
  - First_project
  - templates
  - First_app
  - Index.html
  - New line below “<!DOCTYPE html>”
- Add “{% load static %}”
- Orient to
  - The line below “{{ insert_me }}”
- Add “<img src="{% static "images/image.png" %}" alt="">”

### CSS dir
- This time make one called “css” follow instructions above
- Call your example file “style.css”
- Orient to this file
- Add “.Bo_1 {border: 1px solid black;}”
- Instead of the image tag orient yourself to the line below the template title tag
- Add “<link rel="stylesheet" href="{% static "css/style.css" %}">”
- Orient to the img tag 
- Add this as an attribute “class="Bo_1"”
- Rough notes
  - https://stackoverflow.com/questions/44026548/getting-typeerror-init-missing-1-required-positional-argument-on-delete
  - https://stackoverflow.com/questions/11164420/django-help-attributeerror-module-object-has-no-attribute-charfield/43137403

## Model Migration
- Orient to
  - first_project 
  - first_app 
  - models.py
  - The line below “# Create your models here.”
- Add
  ```
  class Topic(models.Model):
      top_name = models.CharField(max_length=264, unique=True)

      def __str__(self):
          return self.top_name

  class Webpage(models.Model):
      topic = models.ForeignKey(
          Topic,
          on_delete=models.CASCADE,
      )
      name = models.CharField(max_length=264, unique=True)
      url = models.URLField(unique=True)

      def __str__(self):
          return self.name

  class AccessRecord(models.Model):
      name = models.ForeignKey(
          Webpage,
          on_delete=models.CASCADE,
      )
      date = models.DateField()

      def __str__(self):
          return str(self.date)
  ```
- Orient to 
  - Terminal
  - Working dir
  - first_project
- Run 
  - “python manage.py migrate”
  - “python manage.py makemigrations first_app”
  - “python manage.py migrate”

## Model add db record
- python manage.py shell
- from first_app.models import Topic
- print(Topic.objects.all())
- t = Topic(top_name="Social Network")
- t.save()
- print(Topic.objects.all())
- quite() 

## Register Admin interface
- Orient to
  - first_project 
  - first_app
  - admin.py
  - The line above “# Register your models here.”
- Add “from first_app.models import AccessRecord, Topic, Webpage”
- Orient to
  - The line below “# Register your models here.”
- Add
  ```
  admin.site.register(AccessRecord)
  admin.site.register(Topic)
  admin.site.register(Webpage)
  ```

## Create superuser
- Orient to 
  - Terminal
- Run 
  - python manage.py createsuperuser
  - Ivan
  - ivan.copeland2015@gmail.com
  - Readyforanything123
- Run 
  - python manage.py runserver
- Orient to
  - http://127.0.0.1:8000/admin 
- Login

## Add db record via admin tool
- Orient to
  - Webpages
  - Add webpage
- Populate form
  - Topic: socal network
  - Name: Google
  - URL: www.google.com
  - Click save

## Add db record via faker
- Orient to
  - Terminal
- Run
  - activate myEny
  - pip install Faker
- Orient to
  - First_project
- Add file “populate_first_app.py”
- Add this content
  ```
  import os
  os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'first_project.settings')

  import django
  django.setup()

  ## FAKE POP SCRIPT
  import random
  from first_app.models import AccessRecord, Webpage, Topic
  from faker import Faker

  fakegen = Faker()
  topics = ['Search', 'Social', 'Marketplace', 'New', 'Games']

  def add_topic():
      t = Topic.objects.get_or_create(top_name=random.choice(topics))[0]
      t.save()
      return t

  def populate(N=5):
      for entry in range(N):
          # get topic for the entry
          top = add_topic()

          # Create the fake data for that entry
          fake_url = fakegen.url()
          fake_date = fakegen.date()
          fake_name = fakegen.company()

          # Create the new webpage entrye.
          webp = Webpage.objects.get_or_create(topic=top, url=fake_url, name=fake_name)[0]

          # Create a fake access record forthat webpage
          acc_rec = AccessRecord.objects.get_or_create(name=webp, date=fake_date)[0]

  if __name__ == '__main__':
      print("populating scripts!")
      populate(20)
      print("population complete!")
  ```
- Orient to 
  - Terminal
- Run 
  - python populate_first_app.py
- Run server

## Architecture
- MTV
- M - data hadler
- T - Template handler
- V - Page main function
- Urls - Url handler

## Database
- Orient to
  - first_project
  - first_app
  - views.py
  - New line below “from django.http import HttpResponse”
- Add
  - from first_app.models import Topic, Webpage, AccessRecord
- Orient to
  - New line below “return render(request, "first_app/index.html", context=my_dict)”
- Update to
  ```
      webpages_list = AccessRecord.objects.order_by('date')
      date_dict = {'access_records' : webpages_list}
      my_dict = {'insert_me':"Hello I am from view.py!!!"}
      return render(request, "first_app/index.html", context=date_dict)
  ```
- Orient to
  - first_project 
  - templates 
  - first_app 
  - Index.html
  - New line below “<img src=...”
- Add
  ```
  <div class="djangotwo">
        {% if access_records %}
          <table>
            <thead>
              <th>Site Name</th>
              <th>Date Accessed</th>
            </thead>
            <tbody>
              {% for acc in access_records %}
                <tr>
                  <td>
                    {{ acc.name }}
                  </td>
                  <td>
                    {{ acc.date }}
                  </td>
                </tr>
              {% endfor %}
            </tbody>
          </table>
        {% else %}
          <p>No access records found.</p>
        {% endif %}
      </div>
  ```
- Run server
- Rough notes
  - https://stackoverflow.com/questions/3597143/php-style-inline-tags-for-python

## Forms
- Orient to
  - first_project 
  - first_app
- Add
  - forms.py
- Orient to 
  - Forms.py
- Add
  ```
  from django import forms

  class FormName(forms.Form):
      name = forms.CharField()
      email = forms.EmailField()
      text = forms.CharField(widget=forms.Textarea)
  ```
- Orient to
  - first_project 
  - first_app 
  - views.py
  - Below the  “from first_app.models import Topic, Webpage, AccessRecord” line
- Add
  - from . import forms 
- Orient to
  - The end of the file
- Add





