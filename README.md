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
 SW-HQ(user/P@ssw0rd_toor)_BR(user/P@ssw0rd)(root/toor_toor) 

ISP(root_toor)

SRV-HQ_BR(user/P@ssw0rd_toor)

CLI_BR/HQ(user/P@ssw0rd)


```
su
vim /etc/hostname
systemctl reboot
```
## b)	Сконфигурируйте адреса устройств на свое усмотрение. Для офиса HQ выделена сеть 10.0.10.0/24, для офиса BR выделена сеть 10.0.20.0/24. Данные сети необходимо разделить на подсети для каждого vlan.

RTR-HQ/BR

config
sh

SW-HQ | SRV-HQ | CLI-HQ | CICD-HQ | SW-BR | SRV-BR | CLI-BR

## c)	На SRV-HQ и SRV-BR, создайте пользователя sshuser с паролем P@ssw0rd

a.	Пользователь sshuser должен иметь возможность запуска утилиты sudo без дополнительной аутентификации.

b.	Запретите парольную аутентификацию. Аутентификация пользователя sshuser должна происходить только при помощи ключей

c.	Измените стандартный ssh порт на 2023.

d.	На CLI-HQ сконфигурируйте клиент для автоматического подключения к SRV-HQ и SRV-BR под пользователем sshuser. При подключении автоматически должен выбираться корректный порт. Создайте пользователя sshuser на CLI-HQ для обеспечения такого сетевого доступа.

```
adduser sshuser
passwd sshuser
P@ssw0rd
P@ssw0rd
echo "sshuser ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
usermod -aG whell sshuser
sudo -i
```
