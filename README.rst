===================
Celerybeat-instance
===================

Overview
========

This is an Ansible role for running celery beat server instances.
The ``celery`` role is a prerequisite.  Note that it does not configure
the schedule, you must do so elsewhere. Use like this::

    dependencies:
    - role: celerybeat-instance
      instance_name: foo
      virtualenv: /usr/local/foo-virtualenv
      program_dir: /etc/myconfigdir
      app: my.module:app
      user: foo
      log_level: info
      program_environment: PYTHONPATH="/etc/myconfigdir"

Variables
=========

- ``instance_name``: A name that will be used in various places (log
  file name, supervisor program name, schedule file name) to identify
  the instance.
- ``virtualenv``: The python virtualenv directory from which celery beat
  will be run.
- ``program_dir``: The directory in which the server should run.
- ``app``: The celery app; python module, colon, variable.
- ``user``: Operating system user. It will be created, and the service
  will be run as this user.
- ``log_level``: Log level. (The log file will be
  ``/var/log/celery/beat-xxx.log``, where ``xxx`` is the
  ``instance_name``.)
- ``program_environment``: Environment variables as accepted by
  ``supervisor``, i.e. a comma-separated list of A="B" items. (It can't
  be named simply ``environment``, because Ansible, at least 1.9, is
  then confused.)

Meta
====

Written by Antonis Christofides

| Copyright (C) 2015 TEI of Epirus
| Copyright (C) 2015 National Technical University of Athens
| Copyright (C) 2016 Antonis Christofides

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see http://www.gnu.org/licenses/.
