ansible-backup-snapshot
=========

This role will install cron to snapshot ec2 instances

Role Variables
--------------

**backup_snapshots**

   This variable should contains all crons
   Example :

    backup_snapshots:
      mongodb:
        tags:
          role: database
          Name: MONGODB0
        instances:
          - i-ad0fcc4b
          - i-56489db2
        dry_run: false
        autoscaling_limit: 1
        root_device: true
        delete_only: false
        cold_snapshot: false
        retention:
          number: 2
          type: w
        cron: "30 2 * * *"
        region: eu-west-1
   
   default: ``{}``

Example Playbook
----------------


    - hosts: servers
      roles:
         - { role: cycloid.backup-snapshot }

License
-------

BSD

Author Information
------------------

Julien Syx at Cycloid.io
