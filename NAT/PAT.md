Jest to typ dynamicznego NAT, w którym poza pulą adresów globalnych wewnętrznych są dodatkowo wykorzystywane numery portów, dzięki czemu wiele adresów z sieci lokalnej wewnętrznej może mieć ten sam globalny adres IP, ale inny port, dzięki czemu ich ruch jest rozróżnialny.

Jest to najczęstszy typ NAT - ISP może nam przyznać 1 adres i wiele portów. Jeśli port jest już zaklepany, to PAT zapewnia, że zostanie użyty następny. Jeśli porty się wyczerpią, to spróbuje tego samego ale z innym adresem IP z puli.

W wypadku protokołów niewykorzystujących TCP ani UDP, PAT i tak sobie jakoś radzi, np. w wypadku wiadomości ICMP echo request wykorzystują Query ID.

##### Konfiguracja PAT opera się na:
Tym samym, co normalna konfiguracja [[Dynamiczny NAT|dynamicznego NAT]], ale przy powiązywaniu listy ACL z pulą NAT należy dodać słowo **`overload`**.

```
R2(config)# ip nat inside source list 1 interface serial 0/1/1 overload
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R2(config)# interface serial0/1/0
R2(config-if)# ip nat inside
R2(config-if)# exit
R2(config)# interface Serial0/1/1
R2(config-if)# ip nat outside
```

