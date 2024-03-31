# ansible

# Notes
When you try and do ansible-pull with vault there are two ways to get it to work

1. You have to put `ANSIBLE_ASK_VAULT_PASS=True` in front of the ansible-pull
2. Add this to a ansible.cfg file:
```yml
[defaults]
ask_vault_pass = True
```

This is the command I currently use
```
ANSIBLE_ASK_VAULT_PASS=True ansible-pull -U https://github.com/thegreatestgiant/ansible.git
```

And when I want to use a specific playbook
```
ANSIBLE_ASK_VAULT_PASS=True ansible-pull -U https://github.com/thegreatestgiant/ansible.git home.yml
```

## Best Install
Try doing one of these two. For some OS's one works and the other doesn't.
```bash
sudo apt install -y pipx git
pipx install ansible-core
```
```bash
sudo apt install -y python3-pip git
pip install ansible-core
```
An alternative is putting the IP address of your server in the inventory and letting the GitHub Action take care of everything

# Contents of Vault files

## Location(s)

- group_vars/all.yml
- roles/ansible_user/templates/vault.j2
- roles/ssh/templates/*
- roles/kavita/templates/rclone.j2
- roles/services/templates/rclone.j2

## Group_vars

```yml
name: ***
user:
  name: "{{ name }}" 
  password: "***"
  home: "/home/{{ name }}"
```

## Vault.j2

This is your vault password

## Templates

This is everything you would want to put in your .ssh directory

## Rclone.j2

This is the contents of my rclone.conf file which you can generate by installing rclone `sudo -v ; curl https://rclone.org/install.sh | sudo bash` and running `rclone config`


# RoadMap

- [x] finnish up ssh
- [x] Do sean_user
- [x] Link ssh to sean_user
- [x] Add all services to services (Go and NPM I think)
- [x] Look at the startup script for another role maybe
- [x] Tie it all together in local.yml
- [x] Add a github action automation

## The github action

The reason I set it up is because I like to spin up a bunch of temporary linode instances.
The way I use it is I put the ip address into the inventory and then it runs, and I then have to remove that ip address because it locks to my automation which runs on root.

