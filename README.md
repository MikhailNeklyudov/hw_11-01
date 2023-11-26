# Домашнее задание Защита сети - Неклюдов Михаил


#Задание 1.
Suricata и fail2bun на nmap -sA не отработала, остальные Suricata отработала. fail2bun является узкоспециализированным средством обнаружения вторжений и не обнаруживаает такие вторжения.
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/ed67b331-0762-444f-825c-e9156e6d756e)
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/e74294dd-c66b-4555-8edf-daddcfaf1095)

На nmap -sT
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/b1625138-cda3-4e37-9052-0a1c7fcd8dd7)
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/5941f71b-84c1-4dfe-8926-231d6e409643)

sudo nmap -sS 
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/467e7daa-afa8-47b1-818f-c9d032fe838f)
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/10ecad55-f9a3-4609-ace0-75db6f90e354)

sudo nmap -sV
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/39f03afe-a886-48fc-baf1-13dbc1b07ddf)
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/bbecbccc-9be8-4b61-a42d-995dc9f3d640)

#Задание 2.
Подбор логина и пароля прошел удачно.
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/42d1c903-c3f8-4236-bce0-9c0a19f16ebc)

После включения fail2bun атакующий сервер отправлен в бан.
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/38f83296-b20f-4020-b548-fed596c4a80f)
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/4d33502d-3031-4360-be4b-6c105d6f1dad)


Suricata проинформировала. 
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/92b73dad-5ab0-4b78-a385-47756913d04b)
