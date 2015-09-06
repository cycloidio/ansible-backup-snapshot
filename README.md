ansible-supervisord
=========

This role will install supervisord and let you configure programs with yaml

Role Variables
--------------

**supervisord_config_location**

   The path where goes the configuration for each program

   default: ``/etc/supervisord/conf.d/``

**supervisord_programs**

   This variable should contains all programs that runs with supervisord
   Example :

    supervisord_programs:
      lisa-api:
        program_name: "lisa-api"
        user: "alivelisa"
        command: "/home/alivelisa/.virtualenvs/lisa-api/bin/python /home/alivelisa/.virtualenvs/lisa-api/local/bin/lisa-api-cli runserver 0.0.0.0:8000"
        autostart: "true"
        autorestart: "true"
        redirect_stderr: "true"
        stdout_logfile: /var/log/supervisor/lisa-api.log
        stderr_logfile: /var/log/supervisor/lisa-api.log
        stopasgroup: "true"
        killasgroup: "true"
   
   default: ``[]``

Example Playbook
----------------


    - hosts: servers
      roles:
         - { role: cycloid.supervisord }

License
-------

BSD

Author Information
------------------

Julien Syx at Cycloid.io
