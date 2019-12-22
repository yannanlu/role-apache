# role-apache
Ansible role for Apache 2.4 with support on virtual hosts.

This role supports multiple virtual hosts via **apache_server_name**. The default virtual host is required which has an empty value for **apache_server_name**. Therefore, the default virtual host should always be the first to be deployed and the last to be undeployed.
