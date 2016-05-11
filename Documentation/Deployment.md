`sudo apt-get install python3 python3-pip python3-dev libpq-dev`

`sudo pip3 install django`

`sudo pip3 install psycopg2`

`sudo apt-get install postgresql postgresql-contrib`

https://wiki.postgresql.org/wiki/First_steps

***

Install nginx, supervisor, and gunicorn ***

Use the supervisor scripts [somewhere] to get it running

Read this: http://michal.karzynski.pl/blog/2013/06/09/django-nginx-gunicorn-virtualenv-supervisor/

nginx should forward the requests to 127.0.0.1:8000, where gunicorn is running a worker (powered by supervisorctl)