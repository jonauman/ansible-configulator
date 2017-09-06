wickes.configulator
==================


Requirements
------------

This role is expected to be run from jenkins. Therefore, it is expected that jenkins will pull down environment variables and templates before running this role. Jenkins workspace should look something like:

```
├── ansible
│   └── roles
│       └── wickes.configulator
├── env_vars
├── filebeat_config
│   └── etc
│       └── filebeat
├── sensu_config
│   └── etc
│       └── sensu
└── wso2_is_config
    └── opt
        └── app
            └── wso2
                └── wso2is
                    ├── lib
                    └── repositories
                        └── config
```

Role Variables
--------------

```configulator__template_basedir``` - The base directory for all your templates. This is the directory where all your configuration templates live. *Defaults to a relative path to the ansible dir (../).*

```configulator__env_vars``` - The direcory where all the environment variables are stored. *Defaults to '../env_vars' relative to the ansible dir.*

```configulator__dest``` - The temporary directory where the merged files from the envsubst command are created. This directory will be cleaned up at the end of the playbook. *Defaults to '/tmp/dest'.* 

```configulator__sources``` - The list of subdirectories in the *template_basedir* to include in the configuration management process. This should be a subset of top level directories in the configuration template git repo.

Dependencies
------------

None. However, wickes.s3 should be included if there are secrets to pull down and decrypt from S3.

Example Playbook
----------------

    - hosts: localhost
      roles:
         - wickes.configulator

License
-------

BSD

Author Information
------------------

Jon Auman <jon.auman@wickes.co.uk>
