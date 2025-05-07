Jest to pierwszy typ pakietu OSPF. Są one wysyłane na adres multicast 224.0.0.5. Jego zadaniem jest:
- wykrywanie sąsiadów OSPF i tworzenie z nimi przyległości
- ogłaszanie parametrów, które muszą być wspólne, by routery były sąsiadami
- wybieranie [[Router desygnowany|routera desygnowanego]] (DR, *Designated Router*) i zapasowego routera desygnowanego (BDR, *Backup Designated Router*) w sieciach wielodostępowych. 

#### Parametry:
1. **Hello interval**
   >Czas, co który są wysyłane pakiety Hello. Domyślnie 10s.
   >`Router(config-if)# ip ospf hello-interval seconds`
2. **Dead interval**
   >Ile czasu interfejs będzie czekał na odbiór pakietu Hello od sąsiada zanim uzna że ten umarł. Jeśli się to stanie, to sąsiad jest usuwany z [[Bazy danych OSPF|LSDB]], a informacja o jego śmierci jest rozsyłana w sieci. Domyślny dead interval to 4 * (Hello interval).
   >`Router(config-if)# ip ospf dead-interval seconds`
3. **[[Identyfikator OSPF|Identyfikator]]**

Interwały Hello są konfigurowane osobno dla każdego interfejsu i rzadko uzasadnione jest ich ruszanie. Długości interwałów muszą się pokrywać wśród sąsiadów by w ogóle utworzyć przyległość.