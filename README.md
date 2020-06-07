# fail2ban-centos7
fail2ban-centos7

```
sudo yum install epel-release
sudo yum install fail2ban

sudo systemctl enable fail2ban

sudo vi /etc/fail2ban/jail.local
```
copy and paste this:
```
[DEFAULT]
# Ban hosts for two hour:
bantime = 7200

# Override /etc/fail2ban/jail.d/00-firewalld.conf:
banaction = iptables-multiport

[sshd]
enabled = true
```

```
sudo systemctl restart fail2ban

sudo fail2ban-client status
Output
Status
|- Number of jail:      1
`- Jail list:   sshd
```

```
fail2ban-client status sshd
output:
Status for the jail: sshd
|- Filter
|  |- Currently failed: 12
|  |- Total failed:     43
|  `- Journal matches:  _SYSTEMD_UNIT=sshd.service + _COMM=sshd
`- Actions
   |- Currently banned: 2
   |- Total banned:     2
   `- Banned IP list:   220.160.111.78 51.75.19.175
```


