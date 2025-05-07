1. **Stan Down**
   >Router jest w tym stanie jeśli nie odebrał od nikogo pakietów [[Hello]]. Przechodzi do stanu Init gdy on sam zaczyna wysyłać pakiety Hello na interfejsach z uruchomionym OSPF.
2. **Stan Init**
   >Router przechodzi w tym stanie czeka na pakiety Hello od sąsiada. W pakietach znajduje się [[Identyfikator OSPF|identyfikator]] routera wysyłającego, który jest zapisywany do lokalnej listy sąsiadów. 
3. **Stan Two-Way**
   >Stan ten zaczyna się gdy router odbiera pakiet Hello ze swoim własnym identfikatorem routera umieszczonym na liście sąsiadów - oznacza to, że sąsiedzi routera "wiedzą" o jego istnieniu. W tym stanie komunikacja jest dwukierunkowa, a na łączach wielodostępowych wybierany jest [[Router desygnowany|DR i BDR]].
4. **Stan ExStart**
   >W sieciach [[Sieci OSPF punkt-punkt|Point to Point]] oba routery decydują który z nich zainincjuje wymianę [[Komunikaty, pakiety OSPF|pakietów DBD]] 
5. **Stan Exchange**
   >Routery wymieniają się już pakietami DBD, a jeśli informacji brakuje to przechodzą do stanu Loading. Pakiety DBD zawierają typ pakietu stanu łącza, adres routera, koszt łącza, numer sekwencyjny...
6. **Stan Loading**
   >Jeśli pakiety DBD są niespójne po wymianie (czyli jeden router widzi sieć tak, a drugi inaczej), wysyłane są LSR i LSU aby uzupełnić brakujące informacje. Potem LSU są wysyłane po zmianie w sieci lub kontrolnie co 30min.
7. **Stan Full**
   >Pełna synchronizacja