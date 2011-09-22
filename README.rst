========
Djenesis
========


What Djenesis Is
----------------

| Djenesis helps you get started working on a django project, either a brand new one, or one that is already in progress.
| Djenesis has no dependencies other than a standard python install.
| Djenesis leverages virtualenv/pip and helps you manage project dependencies.
| Djenesis allows you to specify your own template, use community templates, or check your project out from your favorite scm (git,svn,hg)


What Djenesis Is Not
--------------------
| Djenesis is not a django app.  It is a python commandline tool.


Usage
-----
::

Usage: djenesis <output_directory> [options] [package...]

Options:
  -h, --help            show this help message and exit
  -e ENV_DIRECTORY, --env-directory=ENV_DIRECTORY
                        Specify the directory to create the virtualenv at
  --no-virtualenv       Don't create a virtualenv
  -t TEMPLATE, --template=TEMPLATE
                        Specify template URL to inflate from


Examples
--------

``djenesis mynewproject``
    | generates ./mynewproject from default template.
    | creates virtualenv at ./env and installs latest Django


``djenesis foobar --no-virtualenv``
    | generates ./foobar from default template.
    | no virtualenv is created.

``djenesis theproject/code --virtualenv=theproject/env Django==1.1 psycopg2``
    | generates ./foobar/code from the default template.
    | initializes a virtualenv at ./foobar/env and installs Django-1.1 and psycopg2

``djenesis mynewproject -e ~/.virtualenvs/mynewproject -t http://example.com/django/random-django-template.tar.gz``
    | downloads and extracts the tar file into ./mynewproject
    | generates a virtualenv at ~/.virtualenvs/mynewproject
    | checks the templates for a requirements.txt, if present will pip install all packages into the virtualenv.

``djenesis mywip/code -e mywip/env -t git+git@github.com:wittyusername/respository.git``
    | uses git to clone the repository into ./mywip/code
    | generates a virtualenv at ./mywip/env
    | if requirements.txt exists at toplevel directory in repo, pip installs any packages present.


Default Project Structure
-------------------------
If you do not specify a template when you invoke Djenesis, it will inflate its default project structure. 
For example if you called the command ``djenesis mynewproject`` the following directory structure would be created::

    ./mynewproject
        ./mynewproject/apps
        ./mynewproject/apps/mainsite/manage.py
        ./mynewproject/apps/mainsite/settings.py
        ./mynewproject/apps/mainsite/settings_project.py
        ./mynewproject/apps/mainsite/settings_local.py.example
        ./mynewproject/apps/mainsite/django.wsgi
        ./mynewproject/apps/mainsite/urls.py
        ./mynewproject/apps/mainsite/views.py
        ./mynewproject/fixtures/
        ./mynewproject/media/
        ./mynewproject/media/uploads
        ./mynewproject/templates/base.html
        ./mynewproject/.gitignore
    ./env
        ./env/lib/**/django


| You'll notice that ``mainsite`` is the default point for all things django related.
| Only the ``apps`` directory is added to the PYTHON_PATH.
| Djenesis automatically created a virtualenv at `./env` and installed the latest version of Django because we specified no other packages.


