Są 3 sposoby na wdrożenie [[QoS]] (*z czego jeden właściwie nie jest QoS*).
1. **Best effort**
   >QoS nie jest jawnie skonfigurowany, po prostu sieć sobie działa i liczymy że nie dojdzie do problemów wymagających priorytetu dla ruchu wrażliwego na czas. W większości przypadków taki model wystarczy i jest najbardziej powszechny. 
2. **InitServ** (usługi zintegrowane)
   >Wysoka jakość, gwarancja dostarczenia pakietów IP. InitServ jawnie zarządza zasobami sieciowymi, zaklepuje pasmo, rezerwuje zasoby, zapewnia QoS dla poszczególnych strumieni. 
   >Każda komunikacja musi wyraźnie określić czym jest i czego potrzebuje, co weryfikuje potem router brzegowy. Aplikacja użytkownika przed wysyłaniem danych żąda określonego rodzaju usługi sieci, a wraz z nim konkretne wymagania dotyczące przepustowości. Jeśli zasobów jest wystarczająco to są one przydzielone. Takie rozwiązanie nie jest jednak skalowalne.
3. **DiffServ** (usługi zróżnicowane)
   > Wysoka skalowalność i elastyczność wdrażania QoS. Urządzenia sieciowe rozpoznają klasy ruchu i na ich podstawie zapewniają różne poziomy QoS. Jest niewiele mniej stabilny od InitServ, ale działa o wiele szybciej i bardziej elastycznie. Nie jest używana żadna sygnalizacja jak wcześniej, polega za to na tym, że elementy są w stanie obsługiwać wiele klas ruchu, gdzie każda ma inne wymagania QoS.