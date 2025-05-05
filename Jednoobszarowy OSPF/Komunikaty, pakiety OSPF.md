**Pakiety stanu łącza** (LSP, *Link State Packets*) to narzędzia używane przez protokół OSPF do określania najszybszej dostępnej trasy dla pakietu. OSPF używa ich do ustanowienia i utrzymania przyległości sąsiadów i wymiany aktualizacji tras. 

#### Pięć typów pakietów OSPF:
1. **Pakiety [[Hello]]**
   >Sprawdza, czy sąsiad istnieje i dalej żyje.
2. **Pakiety opisu bazy danych (DBD, *DataBase Description*)**
   >Zawiera skróconą listę [[Bazy danych OSPF|LSDB]] routera wysyłającego, po czym jest porównywany z lokalną bazą LSDB routera odbierającego. Służy do synchronizacji bazy danych topologii między routerami w całym obszarze.
3. **Pakiety żądania stanu łącza (LSR, *Link State Request*)**
   >W przypadku gdy bazy LSDB nie są identyczne, LSR służy do requestowania więcej informacji.  Żąda określonych rekordów stanu łącza z routera do routera.
4. **Pakiet aktualizacji stanu łącza (LSU, *Link State Update*)**
   >Odpowiedź na LSR lub ogłoszenie nowych informacji, takich jak zmiana stanów łączy. Komunikaty LSU składają się z wielu LSA (Link State Advertisement).
   >
   >![[Pasted image 20250505231510.png]]
5. **Pakiet potwierdzenia stanu łącza (LSAck, *Link State Acknowledgement*)**
   >Odpowiedź od routera wysyłającego LSR na otrzymane LSU. LSAck nie niesie żadnych informacji poza potwierdzeniem.