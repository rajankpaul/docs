---
layout: default
title: Flask 
---

# Flask

> microservice webserver

```
sudo vim config.py
```

```
import os
basedir = os.path.abspath(os.path.dirname(__file__))


class Config(object):
    DEBUG = False
    TESTING = False
    CSRF_ENABLED = True
    SECRET_KEY = 'this-really-needs-to-be-changed'


class ProductionConfig(Config):
    DEBUG = False


class StagingConfig(Config):
    DEVELOPMENT = True
    DEBUG = True


class DevelopmentConfig(Config):
    DEVELOPMENT = True
    DEBUG = True


class TestingConfig(Config):
    TESTING = True
```

```
sudo apt install python3-pip
pip3 install autoenv
sudo vim .env
#source env/bin/activate
#export APP_SETTINGS="config.DevelopmentConfig"
```

## Virtal Environments

### venv (Python 3)
```
sudo apt-get install python3-venv
mkdir myproject
cd myproject
python3 -m venv venv
. venv/bin/activate
```

### virtualenv (Python 2)

```
sudo apt-get install python-virtualenv
python2 -m virtualenv venv
. venv/bin/activate
```

## Installation

```
sudo pip3 install Flask
sudo venv/bin/python3 -m pip install Flask
sudo sh -c 'sudo pip freeze > requirements.txt'
```

[back](../)
