Domyślnie, wszystkie [[Komunikaty, pakiety OSPF|komunikaty OSPF]] są wysyłane przez wszystkie interfejsy biorące udział w protokole OSPF, nawet gdy wiadomo, że po drugiej stronie już nie być routera, który te wiadomości odbierze. Niepotrzebnie zaśmieca to ruch i powoduje problemy z bezpieczeństwem. 

Interfejs pasywny to taki, który nie odbiera pakietów [[Hello]], a więc nie próbuje utworzyć sąsiedztwa, ale nadal reklamuje sieć, do której jest przypięty. Pozwala reszcie OSPF routować do swojej sieci, ale nie próbuje "przedłużyć" routingu dalej.

Żeby uczynić interfejs pasywnym, należy użyć polecenia `passive-interface`

```
R1(config)# router ospf 10
R1(config-router)# passive-interface loopback 0
```

