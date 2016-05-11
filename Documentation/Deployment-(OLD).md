### Install all dependencies

* Python 3
 * Using brew: `brew install python3`
 * Website: [python.org/downloads](https://www.python.org/downloads/)
* PostgreSQL Server
 * Using brew: `brew install postgresql` 
 * Website: [postgresql.org/download](http://www.postgresql.org/download/)
* PostgreSQL Python
 * Using pip: `pip3 install postgresql`
* Django (Currently 1.7.3)
 * Using pip: `pip3 install django==1.7.3`
* UUID
 * Using pip: `pip3 install uuid`

### Set up PostgreSQL
...with a database and login of your choosing. You will enter whichever names and passwords you choose into the project settings.
 - If $`psql` does not let you connect because brew didn't create a database for you, run $`createdb`

### [Download](https://github.com/ezfe/March-Intensive-Placement/archive/master.zip) the repository
### Open `mip/settings.py` and edit the following items.
```py
'NAME': '<database name>',
'USER': '<username>',
'PASSWORD': '<password>',
'HOST': 'localhost',
'PORT': '5432',
```
### Run `python3 manage.py migrate`
### Run `python3 manage.py runserver`