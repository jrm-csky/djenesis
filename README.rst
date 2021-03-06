Description
===========
Djenesis begets django projects.

More speficically it is a commandline utility that helps you either inflate a new django projects from a template, or setup a new work environment for an existing project. It can also automatically manage virtualenv environments and requirements.txt in the template or project.

Basic Usage
===========

New Project From Django Core Template
--------
The most basic form of djenesis, you give it a new project name, and it creates a new django project.

    $ djenesis mynewprojectname

djenesis will create a virtualenv named ``env-mynewprojectname``, install the latest version of django, and run django-admin.py startproject mynewprojectname. 
All you have to do now is 
    $ env-mynewprojectname/bin/python mynewprojectname/manage.py runserver
And you are running django!


New Project From Project Template
--------
Most people have worked out a particular project structure that they prefer for their django projects.
Inflating from a scm repository is a convient way to maintain and manage a project template struture.

    $ djenesis projectname git+https://github.com/concentricsky/csky-django-template.git

this will inflate a new project based on the template found at the git+url in a directory named ``projectname`` 
This will also create a virtualenv named ``env-projectname`` and install any packages found in requirements.txt found at the toplevel directory in the template.


New Work Environment For Existing Project
-------
Often a django project already exists and you need to get a copy up and running to make your changes.
Inflate from an existing django project template and initialize a virtualenv based on requirements.txt

    $ djenesis projectname -i git+git@github.com:user/project.git

this will initialize a virtualenv ``env-projectname`` and clone the project into ``projectname``, just like without -i but will preserve .git or any other SCM management files. (.hg, .git, .svn)



Arguments
=========

Usage: djenesis <output_directory> [options] [template]

Options:
  -h, --help            show this help message and exit
  -e ENV_DIRECTORY, --virtualenv=ENV_DIRECTORY
                        Specify the directory to create the virtualenv at
  -n, --no-virtualenv   Don't create a virtualenv
  -i, --initialize      Initialize from an existing project (dont remove scm files)
