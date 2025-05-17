Przy warstwie łącza fizycznego WAN istnieją terminy używane do opisu połączeń między abonentem a dostawcą usług WAN. 

![[Pasted image 20250516122808.png]]

| Termin                                                              | Opis                                                                                                                                                           |
| ------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DTE** (*Data Terminal Equipment*) – Urządzenie końcowe            | Urządzenie użytkownika, które łączy sieć LAN z urządzeniem komunikacyjnym WAN. Hosty w LAN wysyłają do niego dane, które dalej trafiają do **DCE**.            |
| **DCE** (*Data Communication Equipment*) – Urządzenie komunikacyjne | Urządzenie po stronie klienta umożliwiające komunikację z siecią WAN dostawcy. Zapewnia fizyczne i logiczne połączenie do infrastruktury WAN.                  |
| **CPE** (*Customer Premises Equipment*) – Urządzenia użytkownika    | Zbiorcze określenie dla urządzeń **DTE** i **DCE**, znajdujących się na granicy między siecią użytkownika a WAN. Mogą być własnością klienta lub dzierżawione. |
| **POP** (*Point of Presence*) – Punkt obecności                     | Punkt, w którym infrastruktura klienta łączy się bezpośrednio z siecią dostawcy. Może to być lokalny węzeł usługowy dostawcy.                                  |
| Punkt demarkacyjny (*Demarcation Point*)                            | Fizyczna granica odpowiedzialności między klientem a dostawcą usług. Może to być np. skrzynka instalacyjna na ścianie budynku.                                 |
| Pętla lokalna (*Local Loop*) – "ostatnia mila"                      | Fizyczne łącze (np. kabel miedziany lub światłowód) prowadzące od punktu demarkacyjnego do centrali dostawcy.                                                  |
| **CO** (*Central Office*) – Biuro centralne                         | Punkt dostępowy dostawcy usług, do którego trafiają lokalne pętle użytkowników i który zapewnia dostęp do reszty infrastruktury WAN.                           |
| Sieć płatna (*Carrier Network*)                                     | Wewnętrzna infrastruktura sieciowa operatora WAN, do której dostęp uzyskuje klient po stronie **POP**.                                                         |
| Sieć dostępowa (*Access Network*)                                   | Fragment sieci WAN, który łączy wielu klientów z punktem dostępowym dostawcy. Może obejmować wiele **POP** i **CO**.                                           |
| Sieć szkieletowa (*Backbone Network*)                               | Wysokoprzepustowa infrastruktura łącząca główne segmenty sieci dostawcy, często z redundancją i dużą niezawodnością.                                           |
