OSPF (*Open Shortest Path First*) to protokół routingu dynamicznego. Wykorzystuje on stan łącza (link-state, prefiks sieciowy, długość prefiksu i [[Koszt routingu|koszt]]) zamiast wektora odległości jak [[RIP]] (*Routing Information Protocol*), dzięki czemu brane pod uwagę są prędkości łączy a nie sama ilość przeskoków.

Wykorzystuje on koncept [[Obszary OSPF|obszarów]], dzięki czemu routing nie musi być przeliczany w całej sieci po każdej zmianie.

Głównym algorytmem używanym w OSPF jest algorytm SPF (*Shortest Path Firs*t, a opiera się na algorytmie Djikstry). Kryterium wybierania trasy jest łączny koszt dotarcia do celu, gdzie każde łącze ma jakiś koszt zależny głównie od jego prędkości.

Najlepsze ścieżki są wybierane i zapisywane w tablicy routingu. Zachowywane są różne informacje w [[Bazy danych OSPF|bazach danych]].

OSPF szybko osiąga [[Proces routingu stanu łącza|zbieżność]] dzięki wysyłaniu odpowiednich [[Komunikaty, pakiety OSPF|komunikatów]], lepiej się skaluje i nadaje do większych sieci.

[[Konfiguracja OSPF]] polega na włączeniu protokołu, ustawieniu obszaru i ustawieniu identyfikatora, ewentualnie modyfikacji innych parametrów.