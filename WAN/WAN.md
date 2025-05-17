WAN to sieć telekomunikacyjne, które obejmuje duży obszar geograficzny, a przynajmniej większy niż LAN. Świadczą usługi na poziomie miast, krajów, nawet kontynentów, pozwalają łączyć wiele sieci LAN lub użytkowników zdalnych.

Zazwyczaj sieci WAN należą do **usługodawców** i wymagają opłaty, wtedy płacimy ISP za połączenie naszego LAN z Internetem, innymi lokacjami lub nawet innymi ISP. Zazwyczaj od ceny zależy przepustowość (mowa tu o SLA - *Service Level Agreement*). Można łączyć się z pojedynczym operatorem albo wieloma, dla każdego SLA należy wynegocjować osobno. Wiele operatorów pozwala równoważyć ruch sieciowy i zapewnia redundancję. Do definiowania pojemności łącza szeregowego używało się systemów:
1. **Łącze T** - używane w NA, łącza T1 do 1,544Mb/s i łącza T3 do 43,7Mb/s
2. **Łącze E** - używane w Europie, łącza E1 do 2,048Mb/s i łącza E3 do 34,368Mb/s
Te standardy odnosiły się do miedzi, teraz mamy światłowód.

Zamiast łączenia się Point-to-Point wykorzystuje się dzisiaj [[Komutacja|komutację]].

Istnieją jeszcze połączenia WAN dedykowane, gdzie całe połączenie należy do jednego klienta.

Do opisu topologii WAN używa się topologii logicznej, bo topologia fizyczna byłaby mega skomplikowane i mija się to z celem. Zazwyczaj kilka z tych topologii się ze sobą łączy, ale dla uproszczenia wyróżniamy:
1. **Punkt-punkt**
   >Lokalizacja A łączy się bezpośrednio z lokalizacją B. Słabo się skaluje. Dawno temu głównie takich używano, żeby zapewnić wcześniej ustaloną ścieżkę od klienta do dostawcy. 
2. **Hub-and-Spoke** (gwiazda)
   >Jeden interfejs routera centralnego (hub) jest używany przez wszystkie routery obwodowe (spoke), na co pozwalają obwody wirtualne i podinterfejsy. Jeden router centralny obsługuje wtedy komunikację w całej topologii, zatem jest pojedynczym punktem awarii.
3. **Dual-homed** (gwiazda podwójna)
   >Podobna do gwiazdy, ale hubów jest dwóch i są ze sobą połączeni, co zapewnia redundancję i load balancing. 
4. **Mesh** (pełna siatka)
   >Każdy z każdym. Najbardziej błędoodporna.
5. **Częściowa siatka**
   >Łączy wiele, ale nie wszystkie lokacje.