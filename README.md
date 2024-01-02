# ansible

## Notes
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

## RoadMap

- [x] finnish up ssh
- [x] Do sean_user
- [x] Link ssh to sean_user
- [ ] Add all services to services (Go and NPM I think)
- [x] Look at the startup script for another role maybe
- [ ] Tie it all together in local.yml
- [ ] Add a github action automation

