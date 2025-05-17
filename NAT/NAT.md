NAT (*Network Address Translation*) służy do tłumaczenia adresów [[Prywatne adresy IPv4|prywatnych]] na publiczne.

Dzięki niemu publiczne adresy IPv4 nie wyczerpały się tak szybko, a sieci wewnętrzne pozostają "ukryte" wobec Internetu. Pozwala też na bardziej elastyczne połączenia z siecią publiczną, a także spójność schematów adresowania.

Niestety, jednocześnie tłumaczenie adresów wiąże się z dodatkową pracą do wykonania przez router, co spowalnia działanie sieci. Mogą się też pojawić problemy przy łączności point to point, a także protokołach tunelowania. 

Adresy pojawiające się w NAT są zazwyczaj konfigurowane na podstawie puli adresów IP, którą określa się w konfiguracji. Zazwyczaj router z NAT umieszcza się na brzegu sieci szczątkowej (czyli między siecią, za którą już nie ma kolejnych sieci a Internetem).

##### Typy adresów w NAT:
1. **Adres wewnętrzny lokalny**
   >Adres *(zazwyczaj)* prywatny w sieci lokalnej, który ulegnie tłumaczeniu NAT (np. `192.168.10.10`), istnieje TYLKO w sieci lokalnej.
2. **Adres wewnętrzny globalny**
   >Adres *(zazwyczaj)* publiczny, który reprezentuje urządzenie w sieci wewnętrznej LAN. NAT tłumaczy adres wewnętrzny lokalny na właśnie ten globalny (np. `209.165.201.226`).
3. **Adres zewnętrzny globalny**
   >Rzeczywisty adres IP przypisany zewnętrznemu hostowi. Zazwyczaj tożsamy z adresem zewnętrznym lokalnym (np. `209.165.201.1`).
4. **Adres zewnętrzny lokalny**
   >Adres IP przypisany zewnętrznemu urządzeniu (np. serwerowi w Internecie) z punktu widzenia sieci LAN. Zazwyczaj ten sam, co adres zewnętrzny globalny, bo chcemy się łączyć z serwerami z adresami publicznymi, zatem po tej stronie już nie ma NAT (np. `209.165.201.1`).
   
**Lokalny - z perspektywy LAN**
**Globalny - z perspektywy sieci zewnętrznej**
**Wewnętrzny - dotyczy urządzenia, które może ulec NAT**
**Zewnętrzny - dotyczy urządzenia docelowego**