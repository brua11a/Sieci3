### Klasyczny dynamiczny NAT
W dynamicznym [[NAT]] adresy publiczne są przyznawane na podstawie żądań, a nie przypisywane na stałe. Kto pierwszy ten lepszy. Jeśli adresy z puli się wyczerpią, to host będzie musiał poczekać aż inny host zwolni ten jakiś adres.

Pula adresów lokalnych wewnętrznych jest określana poprzez [[Lista ACL|listę ACL]].
Pula adresów globalnych wewnętrznych jest określana poprzez pulę NAT.  

![[Pasted image 20250513163641.png]]
##### Konfiguracja NAT dynamicznego opera się na:
1. Zdefiniowaniu puli adresów (zazwyczaj publicznych), które będą używane do tłumaczenia.
   >`R2(config)# ip nat pool NAT-POOL1 209.165.200.226 209.165.200.240 netmask 255.255.255.224`
   >- `NAT-POOL1` to nazwa puli
   >- `209.165.200.226 209.165.200.240` to zakres adresów do przydzielenia
   >- `netmask 255.255.255.224` określa która część to sieć a która to host
2. Zdefiniowaniu puli adresów (prywatnych), które będą tłumaczone jako listę ACL, wystarczy [[Numerowane standardowe listy ACL|standardowa numerowana]]. 
   >`R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255`
   >- `1` to numer listy ACL, można zamiast tego zrobić listę [[Nazwane standardowe listy ACL|nazwaną]]
   >- `permit 192.168.0.0 0.0.255.255` określa zakres adresów, które mogą ulec translacji
3. Powiąż ACL z pulą NAT, żeby adresy z ACL były tłumaczone na adresy z puli
   >`R2(config-if)# ip nat inside source list 1 pool NAT-POOL1`
   >  - `source list 1` to zastosowanie listy ACL wcześniej stworzonej, akurat tutaj numerowanej
   >  - `pool NAT-POOL1` to zastosowanie puli NAT wcześniej stworzonej
   >    *\*może to być pojedynczy interfejs, wtedy używa się `interface [interface]`*
4. Określenie interfejsu wewnętrznego i zewnętrznego - który "styka" się z siecią LAN a który z Internetem. Interfejs musi być w tej samej sieci, co adres przed lub po tłumaczeniu.
   >```
   >R2(config)# interface serial 0/1/0
R2(config-if)# ip nat inside
R2(config)# interface serial 0/1/1
R2(config-if)# ip nat outside
>```

___
### [[PAT]]
