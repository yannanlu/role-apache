# role-apache
Ansible role for Apache 2.4 with support on virtual hosts.

In order to use this role, some of the variables are required to be specified or defined, such as **web_frontend** and **apache_bind_ip**. For other variables, please overwrite them as your needs.

| Name                         | Value                | Description                    | File              |
| ---                          | ---                  | ---                            | ---               |
| apache_server_name           | ''                   | name of default virtual server | defaults/main.yml |
| apache_user                  | apache               | username of the installation   | defaults/main.yml |
| apache_group                 | apache               | group name of the installation | defaults/main.yml |
| apache_dir                   | /etc/httpd           | home directory                 | defaults/main.yml |
| apache_conf_dir              | /etc/httpd/conf      | directory for configurations   | defaults/main.yml |
| apache_site_dir              | /etc/httpd/conf.d    | directory for site configs     | defaults/main.yml |
| apache_modsdir               | /etc/httpd/modules   | directory for Apache modules   | defaults/main.yml |
| apache_logdir                | /var/log/httpd       | directory for logs             | defaults/main.yml |
| apache_default_doc_root      | ''                   | document root of default host  | defaults/main.yml |
| apache_doc_root              | ''                   | document root of virtual host  | defaults/main.yml |
| apache_conf_file             | ''                   | config file of the virtual host| defaults/main.yml |
| apache_rolename              | ''                   | name of ansible role of webapp | defaults/main.yml |
| apache_cert_file             | ''                   | cert file for the webapp       | defaults/main.yml |
| apache_key_secret            | xxxx                 | secret of key file for webapp  | defaults/main.yml |
| apache_protected_location    | /                    | location protected by password | defaults/main.yml |
| apache_passwd_file           | ''                   | file for username/password     | defaults/main.yml |
| apache_ldap_url              | ''                   | url for ldap auth provider     | defaults/main.yml |
| apache_ldap_user             | web_services         | username for ldap query        | defaults/main.yml |
| apache_ldap_passwd           | xxxx                 | password for ldap query        | defaults/main.yml |
| apache_pkg_name              | httpd                | name of apache package         | defaults/main.yml |
| apache_version               | 2.4.6-67.el7         | version of apache package      | defaults/main.yml |
| apache_apr_util_ldap_version | 1.5.2-6.el7          | version of apr_util_ldap rpm   | defaults/main.yml |
| apache_locations             | []                   | proxies for backends           | defaults/main.yml |

This role supports multiple virtual hosts via **apache_server_name**. In order to proxy the requests for backend webapps, the value of **apache_server_name** can not be an empty string.

This role provides a template for server.conf to cover most of the use cases. If you want to use your own template to configure your virutal host, you can overwrite the value of **apache_conf_file**. Please make sure it is a template file with the extention of __**.j2**__ appened to the value of **apache_conf_file**.

SSL is always enabled. Therefore, there are two sets of SSL certificates provided for the default virtual server by this role. By default, a self-signed certificate of **server.crt** is used.

Some web applications may need their own certificates for the web frontend. The variable of **apache_cert_file** is reserved for web applications. Therefore just set the proper value for **apache_cert_file** and reference it and its key file in the server configure files. Please make sure the certificate file has the extention of __**.crt**__ and the template file for the key shares the same base name plus the extention of __**.key.j2**__.

## Status

Tested on images of RHEL 7.3 with either Ansible Core 2.6.

## See Also
* [Ansible Docs] (http://docs.ansible.com)
* [role-tomcat] (https://github.com/yannanlu/role-tomcat)
