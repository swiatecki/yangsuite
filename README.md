YANG Suite
==========

YANG Suite core Django application.

Capable of dynamic discovery of installed application plugins.
Provides common library APIs for logging, filesystem access,
GUI appearance and behavior, and client-server communication.

- Authors:  Michael Ott and the other members of yang-suite-dev@cisco.com
- Supports: Python 3.6, Python 3.7, Python 3.8

YANG Suite can be installed as a Docker container or through Python
package management.  Docker-compose is the recommended install.

Requires about 3.5GB of memory to load large Cisco native models.

Docker Installation
-------------------

To ensure you have the latest release of the YANG Suite Docker container files,
from a terminal or PowerShell window, git clone git@github.com:CiscoDevNet/yangsuite.git

WARNINGS:
- Change admin username/password default in docker-compose.yml file first!
- Official SSL/TLS certificate/key needs to be obtained and copied to yangsuite/docker/nginx directory

Self-signed Certificate for testing
-----------------------------------

The SSL/TLS certificates installed with the nginx container should be obtained or generated using a trusted
certificate authority.  As a convenience you can use the yangsuite/docker/ngins/gen_test_certs.sh script to
generate a self-signed certificate/key to get you going quickly.

After obtaining or generating a certificate/key, run this command in the yangsuite/docker/ directory:

    docker-compose up

The yangsuite/docker/yangsuite/production.py file contains Django settings.

Adding/Updating plugins can be done through the Admin-->Manage plugins page or by copying
the plugin wheels into the yangsuite/docker/yangsuite/ directory, uncomment the appropriate
lines in the yangsuite/docker/yangsuite/dockerfile, and run:

    docker-compose up --build

Access docker with web browser
------------------------------

- Connect to https://localhost NOTE: You will get a complaint about the certificate if it was generated using "gen_test_certs.sh"
- Login using default user. You should change this after your first login.

Python Virtualenv Installation
------------------------------

WARNING: You will not have HTTPS support unless you install a web server like NGINX and frontend it with uwsgi.
Instructions for that can be found searching online.

- Create a python 3.6, 3.7, or 3.8 virtural environment and activate it.
- Type ``pip install yangsuite[core]``
- You will be prompted to set superuser credentials.
- Use ctrl-c to stop the yangsuite server
- Use ``yangsuite`` to start the yangsuite server
- Connect to http://localhost:8480.
- Login using user set at install.

Installation with pyATS
-----------------------

- Create a python 3.6, 3.7, or 3.8 virtural environment and activate it.
- Type ``pip install pyats[full]``
- Type ``pip install yangsuite[core]``
- You will be prompted to set superuser credentials.
- Type ``yangsuite`` to start the yangsuite server.
- Connect to http://localhost:8480.
- Login using user set at install.

Configuring yangsuite Server
----------------------------

- Activate the virtual environment
- Type ``yangsuite -h``
