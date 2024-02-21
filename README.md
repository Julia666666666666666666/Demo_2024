# Demo_2024
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
