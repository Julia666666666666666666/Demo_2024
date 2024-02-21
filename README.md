# Demo_2024
![image](https://github.com/Julia666666666666666666/Demo_2024/assets/148867585/a71144c8-fc18-4933-b6c6-b6d87e91b2c0)


## a)	Настройте имена устройств согласно топологии (RTR-HQ/BR)
Cначала устанавливаем новый пароль
```
1-password 12345
2-commit
```
a.	Используйте полное доменное имя
```
config
hostname rtr-hq
do commit
do confirm
```
### SW-HQ(user/P@ssw0rd_toor)_BR(user/P@ssw0rd)(root/toor_toor) 
```
ISP(root_toor)
SRV-HQ_BR(user/P@ssw0rd_toor)
CLI_BR/HQ(user/P@ssw0rd)
```

```
su
vim /etc/hostname
systemctl reboot
```
## b)	Сконфигурируйте адреса устройств на свое усмотрение. Для офиса HQ выделена сеть 10.0.10.0/24, для офиса BR выделена сеть 10.0.20.0/24. Данные сети необходимо разделить на подсети для каждого vlan.

SW-HQ | SRV-HQ | CLI-HQ | CICD-HQ | SW-BR | SRV-BR | CLI-BR

sed -i 's/DISABLED=yes/DISABLED=no/g' /etc/net/ifaces/ens18/options
sed -i 's/NM_CONTROLLED=yes/NM_CONTROLLED=no/g' /etc/net/ifaces/ens18/options
echo 10.0.20.2/24 > /etc/net/ifaces/ens18/ipv4address
echo default via 10.0.20.1 > /etc/net/ifaces/ens18/ipv4route
systemctl restart network
ping -c 4 8.8.8.8
