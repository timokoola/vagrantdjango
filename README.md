# vagrantdjango

Ansible playbook to create a Vagrant box ready for Django project

## Installs

- Postgres
- Nginx
- Uwsgi
- Supervisord
(- Memcached)

## Structure

- group_vars/
	- all: variables for all roles
- roles/
	- common/
		- tasks/
			- main.yml: updates cache, sets up repositories, installs prerequisites, creates users on system
	- nginx/
		- tasks/
			- main.yml: installs and configures nginx
		- templates/: virtual host files etc.
		- handlers/
			- main.yml: handles starting and restarting nginx
	- postgres/
		- tasks/
			- main.yml: installs postgres, copies config over and creates necessary users
		- templates/
		- handlers/
			- main.yml: handles starting and restarting postgres
	- uwsgi/
		- tasks/: 
			- main.yml: sets ups and configures uwsgi and supervisord
		- templates/
		- handlers/
			- main.yml: handle restarting through supervisord
	- django/
		- tasks/ 
			- main.yml: sets up virtualenv, installs all necessary Python libraries and Django
	(- memcached/):
- vagrant_setup.yml: sets up the environment on vagrant
- aws_setup.yml: sets up an amazon environment
- deploy.yml: skeleton deploy the application playbook
- test.yml: tests the set up



