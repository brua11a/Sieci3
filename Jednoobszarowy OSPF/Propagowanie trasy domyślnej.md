Jeśli już korzystamy z routingu dynamicznego to zazwyczaj chcemy jak najmniej tras ustawiać ręcznie. Trasa statyczna może jednak się okazać konieczna np. przy wyjściu do Internetu. W takiej sytuacji router *brzegowy systemu autonomicznego* korzystający z OSPF powinien **propagować trasę domyślną** do pozostałych routerów w sieci.

**Żeby do tego doszło, należy:**
1. Ustawić IP na interface (jeśli jeszcze nie zrobione)
   >`R2(config)# interface lo1`
   >`R2(config-if)# ip address 64.100.0.1 255.255.255.252`
2. Ustawić trasę domyślną
   >`R2(config)# ip route 0.0.0.0 0.0.0.0 interface`
3. Zmienić router na *źródło informacji o trasie domyślnej* w aktualizacjach OSPF
   >`R2(config)# router ospf 10`
   >`R2(config-router)# default-information originate`
   
Po wykonaniu tych operacji pozostałe routery OSPF powinny w swoich tablicach routingu mieć trasę statyczną, ale "nauczoną" poprzez OSPF.

![[Pasted image 20250507112030.png]]

Na tym przykładzie `10.1.1.6` to IP interfejsu wejściowego routera pozwalającego przejść do Internetu innym interfejsem (konkretniej lo1).
