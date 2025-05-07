---
tags:
  - konfiguracja
---
Protokoły routingu dynamicznego wykorzystują *metrykę* do wybrania najlepszej trasy dla pakietu, gdzie większa metryka oznacza dłuższą/wolniejszą trasę. Metryką w [[OSPF]] jest *koszt ścieżki* - im niższy tym lepiej. Koszt ścieżki składa się ze wszystkich kosztów interfejsów po drodze do celu.

Koszt interfejsu maleje wraz z wzrostem prędkości pasma interfejsu. Ze względu na to, że koszt musi być liczbą całkowitą, nowsze, szybsze interfejsy wszystkie mają koszt zaokrąglony do 1. Żeby to zmienić, można koszt ustawić ręcznie (ostrożnie) albo zmienić prędkość odniesienia (lepsze ale trzeba to zrobić konsekwentnie w całej sieci).

![[Pasted image 20250507104543.png]]

Domyślny koszt odniesienia 100,000,000bps, czyli 100Mbps. Żeby go zmienić tak, by sprawiedliwie traktował szybsze łącza od Fast Ethernet, należy użyć komendy na routerze:

```
Router(config)# router ospf 10
Router(config-router)# auto-cost reference-bandwidth Mbps
```

Gdzie *`reference-bandwidth`* to prędkość odniesienia - domyślnie 100, ale można zmienić na 1000 albo 10000. 

Można też ręcznie zmienić koszt interfejsu jeśli np. chcemy zapobiec sytuacjom, w których inny dostawca inaczej od nas liczy OSPF a my chcemy mimo to być z nim połączeni. Można też to zrobić żeby potraktować łącze jako zapasowe. Robimy to:

```
R1(config)# interface g0/0/1
R1(config-if)# ip ospf cost 30
```

