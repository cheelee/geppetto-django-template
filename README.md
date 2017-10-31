<p align="center">
  <img src="https://github.com/tarelli/bucket/blob/master/geppetto%20logo.png?raw=true" alt="Geppetto logo"/>
</p>

# Geppetto Django Template
Geppetto Django Template provides a template to develop a Geppetto Instance in Python. This Django application illustrates how to integrate the pygeppetto_server (https://github.com/MetaCell/pygeppetto-django), a module which provides the basic functionality, and stablishes the framework to customize Geppetto.

This template provides a very basic python infrastructure to serve the static content. The static content (JS + HTML) can be found at org.geppetto.frontend (https://github.com/openworm/org.geppetto.frontend) and the same module is reused for the Geppetto Java Version. Note, however, that the python server implemention is a work in progress and some features has not been migrated yet from Java.

## Installation
pip install django
pip install channels
pip install asgi_redis

**Install redis server (Needed for the sockets communcation)**
sudo apt-get install redis-server
brew install redis


## Features

**Integration with pygeppetto-django**
This module implements the basic functionality to start a Python Geppetto Instance. To integrate pygeppetto-django module, the following actions have been performed:
- Add "pygeppetto_server" to your INSTALLED_APPS setting (settings.py) like this::

    INSTALLED_APPS = [
        ...
        'pygeppetto_server',
    ]

- Include the pygeppetto_server URLconf in your project urls.py like this::

    url(r'^', include('pygeppetto_server.urls')),

- Add routing for the sockest like this:

include('pygeppetto_server.routing.server_routing', path=r"^/org.geppetto.frontend/Geppetto"),

- Add channels and rest framework application to your INSTALLED_APPS setting (settings.py) like this::
INSTALLED_APPS = [
        ...
    'channels',
    'rest_framework',
        ]

        

//3. Run `python manage.py migrate` to create the polls models.

//4. Start the development server and visit http://127.0.0.1:8000/admin/
   to create a poll (you'll need the Admin app enabled).

//5. Visit http://127.0.0.1:8000/polls/ to participate in the poll.


https://github.com/MetaCell/otree-core/tree/d14a37cd3ef63c001a976e87e25669751a459d72/otree/channels
https://blog.heroku.com/in_deep_with_django_channels_the_future_of_real_time_apps_in_django
https://realpython.com/blog/python/django-rest-framework-quick-start/

**What is missing?**

This template is not connected to any database but, as it is implement on top of the django server, this is quite simple to achieve. In the settings.py you will find commented out the binding for the sqlite dbs provided by default with Django. These are two links with some useful tips to start with:
https://docs.djangoproject.com/en/1.11/topics/install/#database-installation
https://docs.djangoproject.com/en/1.9/ref/settings/#databases

