Ansible role for Security Monkey install on AWS Linux
---

Ansible role for Netflix Security Monkey install on AWS Linux. May work on CentOS 6 and 7.

Security Monkey is an open source project developped by Netflix. This role has been made following the official [Quickstart guide](https://github.com/Netflix/security_monkey/blob/develop/docs/quickstart.md) and use dependencies made for this goal.

# Role variables

```yaml
---
# Secmonkey config variables
secmonkey_url: secmonkey.example.com
secmonkey_rds_dnsrecord: dbsecmonkey.xxxxxxxxx.us-west-1.rds.amazonaws.com
secmonkey_db_password: mypassword
secmonkey_db_username: myusername
secmonkey_secretkey: randomstring
secmonkey_password_salt: randomstring
secmonkey_mail_username: mailusername
secmonkey_mail_password: mailpassword
secmonkey_mail_server: email-smtp.us-west-1.amazonaws.com

# SSH variables
ssh_config_path: ~/.ssh/config
host: all
whoami: ec2-user # Host main account (ec2-user for AWS, vagrant for vagrant box)

# Sec monkey env variables
executable_path_virtualenv: /usr/local/src/security_monkey/venv/bin
python_path_virtualenv: /usr/local/src/security_monkey/venv/bin/python
security_monkey_path: /usr/local/src/security_monkey
security_monkey_webui_release: https://github.com/Netflix/security_monkey/releases/download/v0.9.2/static.tar.gz
```

# Dependencies

* Mallear.yum
* Mallear.nginx-el
* Mallear.supervisord-aws-linux

# Example

```yml
- hosts: localhost
  remote_user: root
  roles:
  - Mallear.security-monkey-aws
```