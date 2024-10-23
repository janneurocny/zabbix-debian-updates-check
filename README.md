# Debian Updates check for Zabbix
Template for Zabbix to check if in Debian based OS updates are available.

## Configuration

In */etc/zabbix/zabbix_agentd.conf* in section *"Option: UserParameter"* add following lines:

```
UserParameter=debian_updates.package,apt-get upgrade -s | grep -c ^Inst
UserParameter=debian_updates.security,apt-get upgrade -s | grep ^Inst | grep -c security
```

Restart Zabbix Agent
```
systemctl restart zabbix-agent
```

Select *Debian Updates check* templete in your Host configuration on Zabbix server.