## django project install and start
pip install django
django-admin startproject mysite

##edit settings.py to add localhost dev
ALLOWED_HOSTS = ['*']

##run dev server
cd mysite
python manage.py runserver 127.0.0.1:8080

##create app
python manage.py startapp polls

## migrate
python manage.py migrate

##models create in  polls/models.py
from django.db import models


class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')


class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)