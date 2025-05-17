Kolejkowanie to narzędzie do zarządzania ograniczeniami, które może buforować, ustalać priorytety i jeśli to konieczne, zmienić kolejność pakietów przed przesłaniem ich do miejsca docelowego.

##### Algorytmy kolejkowania:
1. **FIFO** (*First In First Out*)
   >Kto pierwszy ten lepszy znamy od Trajdosa. Nie jest brany pod uwagę żaden priorytet czy [[Klasyfikacja i oznaczanie|klasy ruchu]], każdy pakiet jest traktowany jednakowo. Najmniej wymagający dla routera, domyślnie używany jeśli nie zostanie skonfigurowany [[QoS]]. Jeśli w sieci nie ma opóźnień to jest zdecydowanie wystarczający.
2. **WFQ** (*Weighted Fair Queuing*)
   >
   >![[Pasted image 20250517170208.png]]
3. **CBWFQ** (*Class-Based Weighted Fair Queuing*)
   >Rozszerza WFQ o obsługiwanie klas zdefiniowanych przez użytkowników, co daje nam większą kontrolę. Klasy ruchu mogą dotyczyć kryteriów dopasowania, protokołów, list [[Lista ACL|ACL]], interfejsów wejściowych... Każda klasa ruchu ma osobną kolejkę, a w każdej kolejce działa algorytm FIFO.  W konfiguracji klasy należy tez określić jak duża może być kolejka, jeśli pakiety się w niej nie zmieszczą to może dojść do odrzucenia ich lub tzw. *tail drop*, gdzie ruch traci cechy swojej klasy i jest traktowany równo.
   >
   >![[Pasted image 20250517170518.png]]
4. **LLQ** (*Low Latency Queuing*)
   >Zapewnia ścisłe kolejkowanie priorytetowe do CBWFQ. Pozwala wysyłać pakiety wrażliwe na opóźnienia przed pakietami w innych kolejkach - mogą się one "wryć" przed wolniejsze pakiety. 
   >
   >![[Pasted image 20250517171100.png]]