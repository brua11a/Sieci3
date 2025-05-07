---
tags:
  - konfiguracja
---
Identyfikator routera OSPF to 32-bitowa wartość w postaci adresu IPv4. Pozwala on na jednoznaczną identyfikację urządzenia w sieci korzystającej z OSPF. Jest on potrzebny, ponieważ każdy [[Komunikaty, pakiety OSPF|pakiet OSPF]] zawiera ID routera źródłowego, zatem każdy router takie ID musi mieć. 

Identyfikator jest potrzebny do zsynchronizowania [[Bazy danych OSPF|LSDB]] w [[Stany operacyjne OSPF|stanie]] Exchange. Router o najwyższym identyfikatorze routera wyśle jako pierwszy stój opis bazy danych DBD.

Identyfikator routera ma też znaczenie podczas procesy wyboru [[Router desygnowany|routera desygnowanego (DR)]] - ten o najwyższym ID stanie się DR, a drugi z kolei BDR (jeśli priorytet interfejsu jest domyślny i/lub taki sam).

#### Identyfikator można ustawić ręcznie albo automatycznie.
1. **Ręczna konfiguracja**
   >ID routera jest wtedy jawnie skonfigurowaną wartością 32-bitową przy pomocy komendy:
   >`R1(config-router)# router-id 1.1.1.1`.
   >Jest to preferowana metoda nadawania ID.
2. **Loopback**
   >Jeśli ID nie zostanie ustawione ręcznie, to nadal jest ono potrzebne. Routery radzą sobie z tym poprzez rozwiązania automatyczne. Jeśli na routerze istnieje interfejs Loopback to jego adres staje się ID routera OSPF. **Na interfejsie Loopback NIE musi być włączony OSPF żeby stał się ID.**
   >`R1(config)# interface Loopback 1`
   >`R1(config-if)# ip address 1.1.1.1 255.255.255.255`
3. **Inny IPv4**
   >Jeśli nie ma ani jawnego ID ani loopback to ID routera OSPF staje się najwyższy adres IP ze wszystkich pozostałych skonfigurowanych interejsach.

Aktywny router OSPF nie pozwoli zmienić ID routera do zresetowania całego protokołu - czyli tak długo, jak ID jest w użyciu (np. do utrzymywania przyległości z sąsiadami), nie zostanie zmieniony nawet jeśli ustawimy inny. 

```
R1# show ip protocols | include Router ID
Router ID 10.10.1.1
R1# conf t
R1(config)# router ospf 10
R1(config-router)# router-id 1.1.1.1
% OSPF: Reload or use "clear ip ospf process" command, for this to take effect
```

**Potrzebny jest reset żeby zmiany weszły w życie.**

```
R1# clear ip ospf process
Reset ALL OSPF processes? [no]: y
*Jun  6 01:09:46.975: %OSPF-5-ADJCHG: Process 10, Nbr 3.3.3.3 on GigabitEthernet0/0/1 from FULL to DOWN, Neighbor Down: Interface down or detached
*Jun  6 01:09:46.975: %OSPF-5-ADJCHG: Process 10, Nbr 2.2.2.2 on GigabitEthernet0/0/0 from FULL to DOWN, Neighbor Down: Interface down or detached
*Jun  6 01:09:46.981: %OSPF-5-ADJCHG: Process 10, Nbr 3.3.3.3 on GigabitEthernet0/0/1 from LOADING to FULL, Loading Done
*Jun  6 01:09:46.981: %OSPF-5-ADJCHG: Process 10, Nbr 2.2.2.2 on GigabitEthernet0/0/0 from LOADING to FULL, Loading Done
R1# show ip protocols | include Router ID
Router ID 1.1.1.1
R1#
```

![[Pasted image 20250506102738.png]]