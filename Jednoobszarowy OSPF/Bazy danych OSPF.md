1. **Baza przyległości** (*Adjacency database*)
   >Tablica sąsiadów routera korzystającego z OSPF również korzystających z OSPF. Każda tablica musi z tego powodu być unikatowa. Można wyświetlić `show ip ospf neighbor`.
2. **Baza stanu łącza** (*Link-state database*, **LSDB**)
   >Tworzy tablicę topologii - wszystkie informacje o routerach w sieci, *graf połączeń*. Wszystkie routery w zbieżnej sieci OSPF powinny mieć ten sam LSDB, czyli wszystkie muszą widzieć tą samą sieć. Można wyświetlić `show ip ospf database`.
3. **Baza przekazywania** (*Forwarding database*)
   >Lista optymalnych tras wygenerowana przez użycie SPF na LSDB. Każdy router będzie miał inną bazą przekazywania. Bazę przekazywania widać w tablicy routingu poprzez `show ip route`.