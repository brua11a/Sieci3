Chroni ruch w warstwach od 4 do 7 poprzez szyfrowanie i bezpieczną wymianę kluczy, a także weryfikację pochodzenia. Elementy IPsec można sobie dobierać wedle uznania i potrzeb:
1. **Protokół**
   >AH (*Authentication Header* - uwierzytelnianie pakietu), ESP (*Encapsulation Security protocol* - szyfrowanie pakietu) lub to i to (powoduje problem z NAT)
2. **Poufność**
   >DES, 3DES, AES, brak...
3. **Integralność**
   >MD5, SHA...
4. **Uwierzytelnianie**
   >IKE (*Internet Key Exchange*), RSA...
5. **Diffie-Hellman**
   >DH1, DH2... zalecane DH14+

Używany chociażby w połączeniach [[VPN]] site-to-site. Pomiędzy urządzeniami bramy w obydwu sieciach tworzony jest bezpieczny tunel, a ruch w LANach jest już nieszyfrowany.

IPsec może wykorzystywać GRE (*Generic Router Encapsulation*) do enkapsulacji protokołów niższych warstw sieciowych, po czym IPsec zabezpiecza wszystko poprzez enkapsulację z szyfrowaniem. Pozwala to na przenoszenie pakietów innych niż unicast w bezpieczny sposób, np. pakietów multicast [[OSPF]].

![[Pasted image 20250517161049.png]]

Do tworzenia wielu sieci VPN w dynamiczny sposób można wykorzystać DMVPN (*Dynamic Multipoint VPN*), który wykorzystując topologię [[wan|hub-and-spoke]] do łączenia centrali z oddziałami. W tym rozwiązaniu pojedynczy interfejs GRE potrafi obsłużyć wiele tuneli IPsec.

Do wygodniejszego konfigurowania IPsec używa się VTI (*IPsec Virtual Tunnel Interface*), gdzie konfigurowany jest interfejs wirtualny do odbierania i wysyłania każdego typu ruchu IP. 