---
tags:
  - konfiguracja
---
Jest to protokół pozwalający nam uzyskać dostęp do komunikatów systemowych. Logi z urządzeń w sieci mogą być wysyłanie i zbierane na jednym centralnym serwerze logów według wcześniej ustalonej konfiguracji - na przykład wysyłane mogą być tylko niektóre logi, a wiadomości debug już nie.

Na podstawie odczytanych na serwerze komunikatów można też tworzyć raporty.

Logi mogą być wysyłane do:
1. Buforu - wtedy są widoczne tylko w wierszu poleceń na urządzeniu
2. Konsoli
3. Terminala
4. Serwera syslog - wtedy są zbierane na stałe

Zazwyczaj syslog jest generowany pod wpływem zdarzeń sieciowych. W logu musi znaleźć się poziom ważności i czego on dotyczy (IP, OSPF, SYS, [[IPsec]], IF). Im niższy poziom, tym bardziej krytyczny jest log.

![[Pasted image 20250518131855.png]]

Poziomy od 0 i 4 oznaczają, że wystąpiła awaria wpływająca na funkcjonalność urządzenia.
Poziom 5 oznacza zdarzenia normalne, ale ważne, takie jak włączenie czy wyłączenie interfejsu.
Poziom 6 to zwykłe informacje, takie jak informacje o umowie licencyjnej.
Poziom 7 wskazuje, że logi zostały wygenerowane przez polecenie `debug`

Przykładowy syslog informujący o tym, że łącze EtherChannel zostało włączone może wyglądać tak:
```
%LINK-3-UPDOWN: Interface Port-channel1, changed state to up
```

Gdzie `LINK` to obiekt, `3` to poziom ważności, zaś `UPDOWN` to *nazwa mnemoniczna* obiektu

W logach nie ma domyślnie czasu, można to zmienić komendą `service timestamps log datetime`, ale zadziała to tylko jeśli ustawimy jawnie zegar ręcznie albo poprzez [[NTP]].

```
R1# configure terminal
R1(config)# interface g0/0/0
R1(config-if)# shutdown
%LINK-5-CHANGED: Interface GigabitEthernet0/0/0, changed state to administratively down
%LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0, changed state to down
R1(config-if)# exit
R1(config)# service timestamps log datetime
R1(config)# interface g0/0/0
R1(config-if)# no shutdown
*Mar  1 11:52:42: %LINK-3-UPDOWN: Interface GigabitEthernet0/0/0, changed state to down
*Mar  1 11:52:45: %LINK-3-UPDOWN: Interface GigabitEthernet0/0/0, changed state to up
*Mar  1 11:52:46: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/0/0,
changed state to up
R1(config-if)#
```

