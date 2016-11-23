---
layout: post
title: How to deploy django apps?
description: deployment of django applications
tags: djnago nginx uwsgi pyenv
comments: false
permalink: How-to-deploy-django-applications
sitemap:
  lastmod: 2016-11-20
---

How to install pyenv
=================
Read instruction from [here](https://github.com/yyuu/pyenv-installer)

```bash
apt-get install curl
apt-get install git
apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils
```

* download installer and run it using bash:

```bash
curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
```

```bash
WARNING: seems you still have not added 'pyenv' to the load path.

# Load pyenv automatically by adding
# the following to ~/.bash_profile:

export PATH="/root/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

* install python 3.5.2 using 

```bash
pyenv update
pyenv doctor
env PYTHON_CONFIGURE_OPTS="--enable-shared" pyenv install -fkv 3.5.2
```

create a virtual env

```bash
pyenv virtualenv 3.5.2 webapp
```

Install app's requirements
=============

```bash
pyenv shell webapp
pip install --upgrade pip
pip freeze
pip install -r requirements.txt
```

How to create uwsgi service?
==============

```bash
vim /etc/systemd/system/uwsgi.service
```

```bash
[Unit]
Description=uWSGI Emperor service

[Service]
#ExecStartPre=/usr/bin/bash -c 'mkdir -p /run/uwsgi; chown user:nginx /run/uwsgi'
ExecStart=/home/user/.pyenv/versions/ctf/bin/uwsgi --http 0.0.0.0:8080 --wsgi-file /home/user/ctf7/portal_backend/wsgi.py --chdir /home/user/ctf7/
Restart=always
KillSignal=SIGQUIT
Type=notify
NotifyAccess=all

[Install]
WantedBy=multi-user.target
```

