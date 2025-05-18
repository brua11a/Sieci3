---
tags:
  - konfiguracja
---
Przydatne (**I WYMAGANE NA FINALU**) będzie wysyłanie bieżącej konfiguracji do serwera TFTP. W tym celu można zapisać konfigurację i przekleić do notatniczka, ale lepiej zamiast tego wykorzystać funkcje wbudowane w urządzenia:

```
R1# copy running-config tftp
Remote host []?192.168.10.254
Name of the configuration file to write[R1-config]? R1-Jan-2019
Write file R1-Jan-2019 to 192.168.10.254? [confirm]
Writing R1-Jan-2019 !!!!!! [OK]
```

Jeśli zamiast tego zrobimy:
```
R1# copy tftp running-config 
```
To konfigurację odzyskujemy

W serwerze TFTP można też przechowywać całe obrazy oprogramowania IOS w celu posiadania kopii zapasowej. Wtedy można przekopiować całą zawartość pamięci flash do serwera TFTP. Warto jednak zobaczyć, czy obraz się tam zmieści - przyda się do tego `show flash0:`, gdzie rozmiar zostanie zapisany w bajtach.

```
R1# copy flash: tftp: 
Source filename []? isr4200-universalk9_ias.16.09.04.SPA.bin
Address or name of remote host []? 172.16.1.100
Destination filename [isr4200-universalk9_ias.16.09.04.SPA.bin]? 
Writing isr4200-universalk9_ias.16.09.04.SPA.bin...
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
(output omitted)
517153193 bytes copied in 863.468 secs (269058 bytes/sec)
```

Ponownie i tutaj zamieniając kolejnością parametry:
```
R1# copy tftp: flash:
```
Odzyskujemy obraz IOS do pamięci flash. Skopiowanie jednak nie wystarczy, należy jeszcze sprawić, żeby maszyna bootowała się z tego obrazu: `R1# boot system ios-image`

