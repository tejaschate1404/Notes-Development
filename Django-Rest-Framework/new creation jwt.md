<h1> Json Web Token </h1>

<h2> Install following command </h2>
<ol>
  <li>run enviromnet</li>
  <li>pip install django</li>
  <li>django-admin startproject jwtAuth</li>
  <li>pip install djangorestframework</li>
  <li>pip install djangorestframework-simplejwt </li>
</ol>
<h2> Add following in setting.py </h2>

REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': (
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    )
}

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'rest_framework',
    'rest_framework_simplejwt',
    'jwtApp',
]

<h2>create a serializer.py and add code </h2>

from django.contrib.auth.models import User
from rest_framework import serializers

class UserSerializer(serializers.Modelserializer):
    class Meta :
        Model = User
        fields = ('id','email','username')
