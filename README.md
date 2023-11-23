# Домашнее задание Уязвимости и атааки на информационные системы - Неклюдов Михаил


#Задание 1.
Список служб.
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/f84c920b-f93a-426a-8565-08a35fb81ce2)


Список уязвимостей для 

ftp vsftpd 2.3.4
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/b452069c-1f70-4e6e-afac-5ddee15a7f58)

irc         UnrealIRCd 
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/d6ad4a48-1c36-46d7-baf6-30afa8ed4520)

rpcbind     2
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/00e56ba7-e7d8-4ffc-8793-0916a5d5dcbd)

#Задание 2.
SYN
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/6a4fed49-2531-49bb-8491-8bad7b9d4223)

FIN
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/3d0e93c6-64e0-4c6c-8182-bd559f76e583)

Xmas
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/e85a8da6-18d6-448f-80c6-467c5aac7e33)

UDP
![image](https://github.com/MikhailNeklyudov/hw_11-01/assets/130427747/a010c4f4-1db7-4b0d-8d5c-824f4885e838)

При сканировании SIN по TCP протоколу был направлен запрос SIN и получен ответ ACK, так были установлены открытые порты и службы. Cканировании с битом FIN, который указывает на конец сеанса TCP, более скрытое, если приходит ответ RST, то порт закрыт, если ответа нет, то порт открыт. При Xmas сканировании отправляется пакет с тремя флагами FIN, PSH, URG, при получени RST порт закрыт, если нет ответа, то открыт, проверется фильруется порт или нет, в ответе выводится. При UDP сканировании сканировании происходит по UDP протоколу.
Ответ сервера RST свидетельствует о том, что порт закрыт. 
