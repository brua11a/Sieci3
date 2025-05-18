---
tags:
  - konfiguracja
---
**LLDP** (*Link Layer Discovery Protocol*) robi to samo, co [[CDP]], ale nie jest rozwiązaniem Ciscowym. Działanie jest bliźniaczo podobne, tak samo jak komendy.

Największa różnica między nimi jest taka, że przy konfiguracji na określonych interfejsach w LLDP trzeba osobno skonfigurować obieranie osobno przesyłanie pakietów LLDP - `lldp transmit` i `lldp receive` na konkretnym interface.

```
R1/S1# conf t
R1/S1(config)# lldp run
R1/S1(config)# interface gigabitethernet 0/1
R1/S1(config-if)# lldp transmit
R1/S1(config-if)# lldp receive
```

Wszystkie inne zasady są identyczne.