# Deploy Django App to Heroku
 
## Usage

* If you don't have git installed, follow this [Tutorial](https://www.atlassian.com/git/tutorials/install-git) and come back here.
* Make a copy of your project or use a seperate git branch.
* Make sure your virtual environment is activated.
* Add your dependencies to requirements.txt by typing in the terminal,
* Check [```requirements.txt```](/fathah/heroku-django/blob/main/requirements.txt) in this repo for required dependencies.
```shell
pip freeze > requirements.txt
```
* Create a ```Procfile``` and paste the following
```
web: gunicorn myproject.wsgi
```

* Add this in settings.py
```python
# Import django-heroku
import django_heroku

# Add the following line at bottom
django_heroku.settings(locals())
```

Add Static root
```python
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```

* [Create a Heroku account](https://signup.heroku.com/)
* [Download Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
* [Configure Django Heroku](https://devcenter.heroku.com/articles/django-app-configuration)


* Run the following commands in the terminal
 ```shell
git init
git add .
git commit -am "first commit"

heroku login
heroku create app_name
git push heroku master
heroku open

heroku run python manage.py migrate
```

If you are cloning a old project, add this before pushing
```shell
heroku git:clone -a appname
```
* Modify the following in ```settings.py```
```python
DEBUG = False
ALLOWED_HOSTS = ['your_app_name.herokuapp.com', 'localhost', '127.0.0.1']
``` 

* If you make edits, then run the following commands,
```shell
git add .
git commit -am "edit"
git push heroku master
```
