ghost-ansible
=============

Ansible playbooks for deploying the Ghost blogging system


Note: [dopy](https://pypi.python.org/pypi/dopy) is required for spinning up the digital ocean instance.


## Modify vars.yml with your settings
```
## Digital Ocean Configuration Options

# Put your Digital Ocean Client ID and API key here
client_id: XXXXXX
api_key: XXXXXX

# You also need to specify which ssh key in Digital Ocean you want to use
ssh_key_id: XXXXXX
droplet_name: 'GhostBlog'
region: 3

## Ghost Configuration Options
ghost_ver: 0.3.0
ghost_port: 80
ghost_url: 'http://{{ ansible_eth0["ipv4"]["address"] }}'
email: Mailgun

# Insert your Mailgun user account and password information
email_user: XXXXXX
email_pass: XXXXXX
```

## Create new Droplet and configure it with Ghost:

```
ansible-playbook -i hosts site.yml
```

## Configure existing Ubuntu server with Ghost:

1. Modify the hosts file putting the IP of your VM after [ghosts]

2. Run the following command to only setup Ghost:

```
ansible-playbook -i hosts site.yml --tags configure
```