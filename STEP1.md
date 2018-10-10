* Install Galaxy Roles for Apache, PHP and MySQL
* Review Development Environement
* Review Web Server Playbook
* Deploy our Development Environement
* Modify the Display Error attribute for Development
* ReDeploy our Development Environment

# Install Galaxy Roles

```bash
ansible-galaxy install geerlingguy.apache geerlingguy.php geerlingguy.mysql
```

# Inventory Listing

```bash
ansible --list-hosts --inventory environments/development/inventory development
```

# Web Server & Database Deployment

```bash
ansible-playbook --inventory environments/development/inventory webserver.yml
ansible-playbook --inventory environments/development/inventory database.yml
```

Accessing the Webserver: http://webserver.dev.vagrant.local/

# Enabling Display Errors

```bash
vi environments/development/groups_vars/main.yml
php_display_errors: "on"
```

```bash
ansible-playbook --inventory environments/development/inventory webserver.yml
```
# Verify Apache running

```bash
ansible -i environments/development/inventory webserver -a 'systemctl is-active httpd'
```