W przeciwieństwie do sieci [[Sieci OSPF punkt-punkt|punkt-punkt]], jest w nich potrzebna elekcja [[Router desygnowany|DR i BDR]] żeby nie zalewać wiadomościami [[Proces routingu stanu łącza|LSA]] całej sieci. Zazwyczaj chcemy, żeby tę rolę pełnił konkretny router, dlatego modyfikujemy jawnie jego [[Identyfikator OSPF|identyfikator]]. 


Po sprawdzeniu komendą `R1# show ip ospf neighbor` możemy zweryfikować stany sąsiadów w sieciach wielodostępowych

| Stan               | Opis                                                 | Co jest wymieniane                                                                                             |
| ------------------ | ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **`FULL/DROTHER`** | Router DR lub BDR tak widzi przyległość z DROTHER    | Hello, aktualizacje, zapytania, odpowiedzi, potwierdzenia - wszystkie [[Komunikaty, pakiety OSPF\|wiadomości]] |
| **`FULL/DR`**      | Router tak widzi przyległość z DR                    | Hello, aktualizacje, zapytania, odpowiedzi, potwierdzenia - wszystkie [[Komunikaty, pakiety OSPF\|wiadomości]] |
| **`FULL/BDR`**     | Router tak widzi przyległość z BDR                   | Hello, aktualizacje, zapytania, odpowiedzi, potwierdzenia - wszystkie [[Komunikaty, pakiety OSPF\|wiadomości]] |
| **`2WAY/DROTHER`** | Router DROTHER tak widzi przyległość z innym DROTHER | Tylko pakiety [[Hello]]                                                                                        |
![[Pasted image 20250507102913.png]]

```
R1# show ip ospf neighbor 
Neighbor ID Pri State Dead Time Address Interface
2.2.2.2 1 FULL/BDR 00:00:31 192.168.1.2 GigabitEthernet0/0/0
3.3.3.3 1 FULL/DR 00:00:39 192.168.1.3 GigabitEthernet0/0/0
R1#
```
Router 1 (DROTHER) jest przyległy do DR i BDR

```
R2# show ip ospf neighbor 
Neighbor ID Pri State Dead Time Address Interface
1.1.1.1 1 FULL/DROTHER 00:00:31 192.168.1.1 GigabitEthernet0/0/0
3.3.3.3 1 FULL/DR 00:00:34 192.168.1.3 GigabitEthernet0/0/0
R2#
```
Router 2 (BDR) jest przyległy do DR i DROTHER

```
R3# show ip ospf neighbor 
Neighbor ID Pri State Dead Time Address Interface
1.1.1.1 1 FULL/DROTHER 00:00:37 192.168.1.1 GigabitEthernet0/0/0
2.2.2.2 1 FULL/BDR 00:00:33 192.168.1.2 GigabitEthernet0/0/0
R3#
```
Router 3 (DR) jest przyległy do BDR i DROTHER