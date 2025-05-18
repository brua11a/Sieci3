Szczegółowy proces może być różny, ale zazwyczaj polega na następujących krokach:
1. **Wejdź w trym ROMMON**
   >Potrzebny do tego będzie dostęp do konsoli i specjalna sekwencja przerw podczas uruchamiania pamięci flash gdy urządzenie jest wyłączone. Jeśli nam się uda, to zobaczymy znak zachęty `rommon 1 >`
   >```
   >Readonly ROMMON initialized
monitor: command "boot" aborted due to user interrupt
rommon 1 > 
   >```
2. **Zmień rejestr konfiguracji**
   >Dzięki poleceniu `confreg` można konfigurować konkretne rejestry, poprzez zmianę ich wartości zmieniane jest zachowanie urządzenia. `confreg 0x2142` sprawia, że urządzenie przy uruchamianiu ignoruje konfigurację startowa. Po zmianie rejestru należy wykonać `reset`.
   >```
   >rommon 1 > confreg 0x2142
rommon 2 > reset
System Bootstrap, Version 15.0(1r)M9, RELEASE SOFTWARE (fc1)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 2010 by cisco Systems, Inc.
(output omitted)
>```
3. **Skopiuj `startup-config` do `running-config`**
   >To już robi się normalnie w urządzeniu
4. **Zmień hasło**
   >`R1(config)# enable secret blablabla`
5. **Skopiuj `running-config` do `startup-config`**
   >Ale przed skopiowaniem ponownie zmień wartość rejestru, tym razem na `0x2102`.
   >```
   >R1(config)# config-register 0x2102
R1(config)# end
R1# copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
R1#
>```
6. **Zrestartuj urządzenie**
   >`R1# reload`