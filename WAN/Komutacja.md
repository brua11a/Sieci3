Komunikacja w sieciach WAN  odbywa się za pomocą *komutacji* (przełączania). Można wykorzystać nawet łącza operatorów sieci telefonicznych.
##### Typy komutacji łączy:
1. **Łączy**
   >Tworzony jest dedykowany kanał lub obwód między punktami końcowymi przed początkiem komunikacji, z którego nie korzysta nikt inny - tworzony jest wirtualny obwód łączący urządzenia końcowe tak, jakby były ze sobą bezpośrednio połączone pomimo tego, że w sieci WAN pomiędzy nimi jest mnóstwo sprzętu. Z tego rozwiązania korzysta PSTN i ISDN. Raczej słabe rozwiązanie.
2. **Pakietów**
   >Dane ruchu są dzielone na pakiety, które są kierowane do sieci używanej przez wielu użytkowników. Nie jest tworzone specjalne połączenie, wielu korzysta z tego samego kanału. Jest to tańsze i bardziej elastyczne. Czasem dane będą musiały czekać na swoją kolej w sprzęcie. Z takiego rozwiązania korzysta Metro Ethernet, MPLS, Frame Relay, ATM.

##### Opis części rozwiązań:
1. **PTSN** (*Public Service Telephone Network*)
   >Tradycyjna sieć telefoniczna. [[Urządzenia specyficzne dla sieci WAN|Modem]] moduluje dane cyfrowe na sygnał analogowy i vice versa. Prędkość ograniczona przez parametry [[Połączenia między abonentem a dostawcą|pętli lokalnej]]. Przestarzała technologia.
2. **ISDN** (*Integrated Services Digital Network*)
   >Umożliwia PTSN przenoszenie sygnałów cyfrowych, dzięki czemu jest szybciej. Też jednak mało popularne bo [[Protokoły WAN|DSL]] jest szybszy i lepszy.
3. **Frame Relay**
   >Służy do zdalnego łączenia lokacji ze sobą. Pojedynczy interfejs routera może służyć do połączenia z wieloma sieciami, dla każdej tworzy wirtualne stałe połączenie. Raczej zastąpione przez Metro Ethernet.
4. **ATM** (*Asynchronous Transfer Mode*)
   >Umożliwia wysyłanie głosów, obrazów, innych danych przez sieci prywatne i publiczne. Dane są zamykane w komórkach ATM, gdzie 5-bajtowy nagłówek określa rodzaj treści. Wymaga przez ten narzut większej przepustowości. 