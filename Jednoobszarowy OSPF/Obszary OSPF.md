[[OSPF]] podlega strukturze hierarchicznej, na którą zezwala wprowadzenie tzw. obszarów (*areas*). 
Obszar w OSPF to grupa routerów, która ma tą samą treść [[Bazy danych OSPF|bazy danych stanu łącza LSDB]] (czyli "pamiętają" i "widzą" dokładnie tą samą sieć). 

#### Dwie implementacje OSPF:
1. **Jednoobszarowy OSPF**
   >Wszystkie routery znajdują się w jednym obszarze, baza danych stanu łącza jest jedna i odpowiada CAŁEJ sieci. Zazwyczaj używamy tutaj obszaru 0 dla wygody.
   >
   >![[Pasted image 20250505224131.png]]
2. **Wieloobszarowy OSPF**
   >OSPF jest implementowany w wielu obszarach w sposób hierarchiczny, gdzie każdy musi być połączony z rdzeniem area 0. Routery łączące obszary to routery międzyobszarowe ABR (*Area Border Routers*). W wypadku zmiany w jednym z obszarów, LSDB zmienia się tylko w tym obszarze, dzięki czemu nie trzeba przeliczać od nowa całej sieci, a tylko jeden obszar i ewentualnie trochę zmienić informacje na temat routingu w pozostałych obszarach.
   >
   >Routing jest dalej wykonywany międzyobszarowo, obszary głównie ograniczają niepotrzebne przeliczania SPF i zmiany LSDB. Dodatkowo, dzięki takiemu rozwiązaniu tabele routingu mogą być mniejsze.
   >
   >![[Pasted image 20250505224533.png]]