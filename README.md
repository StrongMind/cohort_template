# Cohorts session 1

## Prerequisites

System with [git](https://git-scm.com/) and [docker compose](https://docs.docker.com/compose/) installed.

Editor or IDE ([PyCharm](https://www.jetbrains.com/pycharm/) recommended, either professional or community) capable of working with python files. I recommend you use the professional trial version.

[Pop](https://pop.com/) in order to pair with other members if not local.

## Setup

In github, [go to the template repository for this class](https://github.com/StrongMind/cohort_template), clone into your personal GitHub.

In WSL2 (windows) or a terminal (Mac)

`git clone <your repo url here> ` where "your repo url here" is the URL of the cloned repository in your account

`docker-compose build`

In PyCharm preferences (you may need to install the docker plugin, before this is available):

* go to your project
* go to "python interpreter"
* click the settings icon next to your interpreter
* click add
* select "Docker Compose" in the left of the dialog
* choose "web" in service and then click "OK"

In WSL2 or a terminal:
* To get a bash prompt inside your docker environment;
  * `docker-compose run web bash`
* To start a new django project
  * `django-admin.py startproject cohort`

Those two steps should have created a new project inside your repository named "cohort". In the future, when we talk about "from a docker bash prompt", you will use `docker-compose run web bash` to get there. 

In PyCharm, right click on the `cohort` folder, then Mark directory as sources root.

Finally, right click on `docker-compose.yml` and click "run docker-compose.yml". (If you decided not to use PyCharm, you would run `docker-compose up` here.)

In a browser, [go to http://localhost:8000](http://localhost:8000). You should now see a welcome page. You now have a django app successfully running.

## Create an app

A django project consists of applications. These can either be applications you create yourself, or applications installed from python packages available on PyPI (the python package repository). Reusable applications are a quick way to get significant chunks of functionality very quickly, as we will show you later.

For now, though, let's start our first application!

From a docker bash prompt:
* `cd cohort`
* `python manage.py startapp forum` this command creates an application in the project named "forum".

In `cohort/settings.py`, you will see an `INSTALLED_APPS` section. This controls which applications a django project has installed. You can see several applications already installed that come as a standard part of django. Let's install our newly created application into this list, by adding "forum" to this list.

## Set Up tests