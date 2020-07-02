Ansible role: os-packages
==================================

Generate and deploy Let's Encrypt SSL certs on a web server. 

Role Variables
--------------

| Name          | Description                                                                                                                              | Type      | Default   | Required   |
| --------------| -----------------------------------------------------------------------------------------------------------------------------------------| :-------: | :-------: | :--------: |
| ssl_webserver | Indicates the name of the webserver in use. This is used to stop and start the service as well as install the appropriate certbot plugin | string    | nginx     | no         |
| ssl_domains   | List of domain objects to generate ssl certs for See: SSL Domains                                                                        | list      | []        | no         |


### SSL Domains

The variable `ssl_domains` is a list of SSL domain specifications. The simplest
form is just `domain: my.domain.com`. A full example with all options is below:

```yaml
ssl_domains:
  # The simplest form this will generate an SSL certificate for example.com with
  # an admin email address of admin@example.com
  - domain: example.com
  # This form demos all options
  - domain: mine.com
    # Specify the admin email for this SSL domain, defaults to admin@{{ domain }}
    admin_email: nope@mine.com
```

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - role: chasinglogic.letsencrypt
```
