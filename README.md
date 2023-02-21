# ansible-worpress-multisite

An Ansible Module to create a Multisite Wordpress Server (Debian 10)

## Instalation

Just create your `vars.yaml` from `vars.yaml.example`

 Configurations: 
 
- `www_path`: Directory where all project will install
- `blog`: A dictionary with all variables for each site
  - **name**. Identifier for the Wordpress instance, we use to set database/files configurations
  - **url**. Domain name for the site
  - **dbpass**. Database's password
  - **wpsecret**. It need it for encryptions session on Wordpress. Random string
  - **enable_https**. To enable HTTPS Support

> If you enable HTTPS support you have to add certs for the blog with Identifier name for the site. 
> Example:
> My ID (`name`) for the site is `myblog`, I put on the directory `src` the follow files: 
> `myblog.crt` and `myblog.key` 

Example of configuration: 

```yaml
---
ansible_python_interpreter: auto_legacy
www_path: '/var/www'
# Support for multisite
blogs: 
  - name: myblog
    url: myblog.lan
    dbpass: devtest
    wpsecret: tEOYnJfkQrroCecwk8Tc1GAt7GzXLSI6 # A ramdom string
    enable_https: false
  - name: anothersite
    url: anothersite.lan
    dbpass: devtest
    wpsecret: vPi[+BvdHXr76KMQP*5Q3%omGubx%q-itT # A ramdom string
    enable_https: false
```

## Testing

We tested this playbook with [Vagrant](https://www.vagrantup.com)

```
$ vagrant up
```

If you need test some updates

```
$ vagrant up --provision 
```

   

