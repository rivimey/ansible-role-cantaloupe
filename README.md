# Ansible Role: Cantaloupe

An Ansible role that installs [Cantaloupe](https://github.com/medusa-project/cantaloupe) in standalone mode. Servlet mode (running in Tomcat) has been removed in this role. 

## Requirements

Tested on Centos 7.

## Role Variables

Version of Cantaloupe to install

    cantaloupe_version: 4.0.2

Where to install Cantaloupe

    cantaloupe_install_root: /opt

Target of symlink from the extracted cantaloupe archive

    cantaloupe_symlink: /opt/cantaloupe

Path to cantaloupe logs

    cantaloupe_log_path: /var/log/cantaloupe

Cantaloupe user

    cantaloupe_user: cantaloupe

Cantaloupe group

    cantaloupe_group: cantaloupe

Where to find properties file cantaloupe.properties

    cantaloupe_properties_path: /opt/cantaloupe/

Command to start cantaloupe with in service file. Note java heap size settings, adjust to taste.

    cantaloupe_start_command: "/bin/java -Dcantaloupe.config={{ cantaloupe_properties_path }}/cantaloupe.properties -Xms2g -Xmx8g -jar {{ cantaloupe_symlink }}/cantaloupe-{{ cantaloupe_version }}.war"

Where to install service file.

    cantaloupe_systemd_path: "/etc/systemd/system/multi-user.target.wants"

Whether to enable admin console with default password (admin). 

    cantaloupe_is_dev: true

Port for Cantaloupe to use.

    cantaloupe_http_port: 8182
  
## Example Playbook

    - hosts: cantaloupe
      roles:
        - cantaloupe

## License

MIT

## Author

Forked from [Islandora-Devops/ansible-role-cantaloupe](https://github.com/Islandora-Devops/ansible-role-cantaloupe) and modified heavily by NYU DLTS
