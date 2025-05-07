---
tags:
  - konfiguracja
---
Pierwszym krokiem jest samo włączenie [[OSPF]] globalnie na całym routerze.
```
R1(config)# router ospf 10
```
Potrzebny jest przy tym *process-id*, który ma tylko lokalne znaczenie i jest raczej dowolny, ale najlepiej wybierać wszędzie ten sam.

Pozwala to przejść do trybu konfiguracji OSPF na routerze, gdzie można skonfigurować opcje protokołu, takie jak [[Identyfikator OSPF|identyfikator routera]] czy [[Obszary OSPF|obszar]]. 

![[Pasted image 20250506235226.png]]

#### Konfiguracja z `network` - na cały router
W trybie konfiguracji protokołu OSPF (po wpisaniu `R1(config)# router ospf 10`) można określić sieci ogłaszane przez router dzięki poleceniu:
`R1(config-router)#` **`network`** *`network-address wildcard-mask`* **`area`** *`area-id`*
- *`network-address`* to adres podsieci
- *`wildcard-mask`* to *wildcard*, [[Maska blankietowa|maska blankietowa]], odwrotność normalnej maski podsieci
- *`area-id`* to obszar, którego dotyczy konfiguracja; tutaj zawsze będzie 0

```
R1(config)# router ospf 10
R1(config-router)# network 10.10.1.0 0.0.0.255 area 0 -- INTERFEJS Lo0
R1(config-router)# network 10.1.1.4 0.0.0.3 area 0 -- INTERFEJS G0/0/0
R1(config-router)# network 10.1.1.12 0.0.0.3 area 0 -- INTERFEJS G0/0/1
R1(config-router)#
```

W konfiguracji odniesienia ten zestaw poleceń każe routerowi rozgłaszać sieci określone w promptach. Interfejsy routera (Lo .1, G0/0/0 .5, G0/0/1 .14) należą do tych sieci, zatem biorą udział w rozgłaszaniu OSPF.

Ewentualnie, zamiast ogłaszać sieci, można włączyć sam interfejs do procesu routingu. Żeby to zrobić, nalezy w poleceniu `network` podać dokładny adres interfejsu i maskę blankietową `0.0.0.0` (*wszystkie bity muszą zostać dopasowane*). Interfejs zostanie włączony do procesu routingu, dzięki czemu proces OSPFv2 zacznie wysyłać w komunikatach sieć dostępną na tym interfejsie.

```
R1(config)# router ospf 10
R1(config-router)# network 10.10.1.1 0.0.0.0 area 0
R1(config-router)# network 10.1.1.5 0.0.0.0 area 0
R1(config-router)# network 10.1.1.14 0.0.0.0 area 0
R1(config-router)#
```

#### Konfiguracja z `ip ospf` - na konkretny interface
Będąc w konfiguracji interfejsu wystarczy wpisać `ip ospf 10 area 0` (gdzie 10 to numer procesu, taki sam lokalnie we wszystkich elementach tego procesu). Jest to funkcjonalnie bardzo podobne do użycia `network` z dokładnym adresem IP interfejsu.
```
R1(config)# interface GigabitEthernet 0/0/0
R1(config-if)# ip ospf 10 area 0
R1(config-if)# interface GigabitEthernet 0/0/1
R1(config-if)# ip ospf 10 area 0
R1(config-if)# interface Loopback 0
R1(config-if)# ip ospf 10 area 0
R1(config-if)#
```
