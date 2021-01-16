<h1 align="center">raspberry-pi-ansible 🍇</h1>
<p align="center">Set of Ansible roles to automate the initial setup I usually do on my Raspberry Pi's.</p>

## Roles
### ⚙️ setup
It just ensures that the ```wheel``` group exists and setup my personal user. I could do a lot more but most of the work is already done manually after the image flashing process when I setup my network settings in the SD's ```boot``` partition.

### 🛡 hardening
Some system security settings:
* file and directories permissions
* restrict ```su``` usage
* setup ```wheel``` group
* login lockout
* iptables rules

Check [tasks](roles/hardening/tasks) for more info.

### 🚫 adguardhome
Install [AdGuardHome](https://github.com/AdguardTeam/AdGuardHome) inside the home of the user set in the ```adguardhome.user_install``` var.

For instance, if
```yaml
adguardhome:
    user_install: nicuz
```
AdGuardHome will be installed under ```/home/nicuz```

## Usage
Customize [raspberrypi.yaml](host_vars/raspberrypi.yaml), then:
```shell
ansible-playbook -i hosts.yaml roles/ROLE_NAME/main.yaml
```