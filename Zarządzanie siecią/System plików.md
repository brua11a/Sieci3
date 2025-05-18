---
tags:
  - konfiguracja
---
Na routerach i switchach znajdują się systemy plików, w których przechowywana jest konfiguracja. Jeśli nie chcemy jej zapamiętywać za każdym razem, można po prostu ją wyświetlić, pobrać i zapisać.

Każde urządzenie będzie miało trochę inną strukturę katalogów, dlatego warto jest ją wyświetlić poleceniem `show file systems`. Znajdziemy tam informacje o ilości pamięci, typu systemu plików, uprawnieniach (`ro`, `wo`, `rw`). Domyślnym systemem plików jest `flash`, na którym będziemy się skupiać obok TFTP i NVRAM. Rozruchowy system IOS też znajduje się w pamięci `flash`, dlatego zawsze od niego zaczynamy.

___

Wpisując polecenie `dir` można wyświetlić zawartość obecnego katalogu, domyślnie jest to pamięć `flash`, konkretnie katalog `bootflash:/`.

Żeby zmienić katalog, należy użyć polecenia `cd` z nazwą katalogu (widzimy je w `show file systems` a więc nie trzeba ich zapamiętywać). Żeby przejść do NVRAM, należy wpisać `cd nvram:`, a następnie `dir` by wylistować zawartość pamięci NVRAM. Znajdziemy tam chociażby dobrze nam znany plik `startup-config`, do którego kopiowaliśmy nieraz `running-config`.

___

W urządzeniach od Cisco są też miejsca na USB, gdzie można podłączyć urządzenia i z nich odczytywać i zapisywać dane jak z systemu plików. Będzie to widoczne w, ponownie, `show file systems`, gdzie zobaczymy `usbflash0:` lub podobne.

Żeby zapisać konfigurację bieżącą w urządzeniu na USB należy posłużyć się `copy running-config usbflash0:`. Bieżąca konfiguracja zostanie skopiowana z pamięci NVRAM do USB. Można to potem zweryfikować poleceniem `dir`, np. `dir usbflash0:/`, a poleceniem `more` i wskazaniem ścieżki do pliku można dowiedzieć się o nim więcej, chociażby zobaczyć zawartość.

```
R1# dir usbflash0:/
Directory of usbflash0:/
    1  drw-     0  Oct 15 2010 16:28:30 +00:00  Cisco
   16  -rw-  5024   Jan 7 2013 20:26:50 +00:00  R1-Config
4050042880 bytes total (3774144512 bytes free)
R1#
R1# more usbflash0:/R1-Config
!
! Last configuration change at 20:19:54 UTC Mon Jan 7 2013 by
admin version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname R1
!
boot-start-marker
boot-end-marker
!
logging buffered 51200 warnings
!
no aaa new-model
!
no ipv6 cef
R1#
```

Przywracane konfiguracji odbywa się w drugą stronę: `copy usbflash0:/R1-Config running-config`.

