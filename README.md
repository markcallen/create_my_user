# create_my_user

Ansible role to:
- Create a user
- Add them to `sudo` and `docker` groups
- Enable passwordless sudo for the `sudo` group
- Install SSH public keys from a GitHub URL
- Fail early if `sudo` or `docker` are not installed

## Variables (pass from playbook)

```yaml
user_name: marka
ssh_key_url: "https://github.com/markcallen.keys"
```

## Example Playbook

Install this playbook

```
ansible-galaxy install git+https://github.com/markcallen/create_my_user.git
```

```yaml
- name: Provision user
  hosts: all
  become: yes
  vars:
    user_name: marka
    ssh_key_url: "https://github.com/markcallen.keys"
  roles:
    - create_my_user
```

```
ansible-playbook -i <hostname>, -u root example_playbook.yml
```
