Jest to pierwszy typ pakietu OSPF. Są one wysyłane na adres multicast 224.0.0.5. Jego zadaniem jest:
- wykrywanie sąsiadów OSPF i tworzenie z nimi przyległości
- ogłaszanie parametrów, które muszą być wspólne, by routery były sąsiadami
- wybieranie [[Router desygnowany|routera desygnowanego]] (DR, *Designated Router*) i zapasowego routera desygnowanego (BDR, *Backup Designated Router*) w sieciach wielodostępowych. 

#### Parametry:
1. hello interval
2. dead interval
3. [[Identyfikator OSPF|identyfikator]]