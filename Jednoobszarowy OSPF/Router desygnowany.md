---
tags:
  - konfiguracja
---
Router desygnowany i zapasowy router desygnowany istnieją w sieciach wielodostępowych by zapewnić synchronizację baz danych routerów. Mówimy o synchronizacji dopiero po ustawieniu przyległości pakietami [[Hello]]. 

![[Pasted image 20250507101834.png]]

Jeśli DR i BDR nie są potrzebne, bo nie jesteśmy w sieci wielodostępowej, wystarczy zadecydować który z dwóch routerów wyśle [[Komunikaty, pakiety OSPF|pakiety DBD]] jako pierwszy - będzie to ten o wyższym [[Identyfikator OSPF|identyfikatorze routera]]. 

Jeśli DR i BDR są potrzebne, a w sieciach wielodostępowych są, to przed przejściem do ExStart dokonywana jest ich elekcja. O tym który router stanie się DR i BDR decyduje najpierw priorytet interfejsu (0-255, im mniejszy tym mniejsza szansa na wybranie, domyślnie 1), a dopiero potem jego [[Identyfikator OSPF|identyfikator]]. Wybieranie routerów DR i BDR odbywa się zaraz po tym, jak pierwszy router, na którego interfejsie włączono protokół OSPF, stanie się aktywny w sieci wielodostępowej.

Priorytet można zmienić poleceniem `ip ospf priority` na pożądanym interface.
```
R1(config)# interface GigabitEthernet 0/0/0
R1(config-if)# ip ospf priority 255
R1(config-if)# end
R1#
```
Priorytet ustawia się na interface, ponieważ DR i BDR są wybierane na poziomie interfejsów - DR i BDR staje się na konkretnym łączu, a nie w całej sieci. Router może być DR w jednej sieci a jednocześnie DROTHER w innej.

Jeśli router o wyższym priorytecie dołączy do sieci, nie "przejmie" on roli DR do restartu całej elekcji. Ewentualnie po awarii DR stanie się on kolejnym BDR.

Zadaniem DR jest zbieranie i dystrybucja wszystkich wysyłanych i odbieranych LSA na adres multicast `224.0.0.5`. DR zbiera i rozsyła **tylko** LSA, routing itd. działa normalnie. Dzięki takiemu rozwiązaniu sieć wielodostępowa nie jest zalewana nadmiarowymi pakietami LSA. 

Routery, które nie są ani DR ani BDR są DROTHER. Te używają adresu multicast `204.0.0.6` by wysyłać pakiety OSPF do DR i BDR, gdzie te dwa nasłuchują.
