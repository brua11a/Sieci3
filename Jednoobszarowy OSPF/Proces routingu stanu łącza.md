Do uzyskania zbieżności i utrzymania aktualnego stanu w bazie stanu łącza ([[Bazy danych OSPF|LSDB]]) potrzebna jest wymiana informacji poprzez routery korzystające z [[OSPF]].
#### Zawiera się ona w 5 etapach:
1. **Ustanowienie przyległości sąsiadów**
   >Polega na wysyłaniu pakietów [[Hello]] ze wszystkich interfejsów na których jest uruchomiony OSPF. Jeśli na tym łączu znajduje się sąsiad i wyśle odpowiedź, router OSPF spróbuje utworzyć z nim [[Stany operacyjne OSPF|przyległość]].
2. **Wymiana [[Komunikaty, pakiety OSPF|komunikatów o stanie łącza]] (LSA)**
   >Po ustanowieniu przylegania routery wymieniają się tym co wiedzą o stanie łącza (*Link State Advertisement*, LSA) ze wszystkimi przylegającymi sąsiadami. Te pakiety zawierają informacje o bezpośrednio połączonych łączach. Po otrzymaniu LSA od jednego routera są one "podawane dalej" aż każdy router będzie wiedział wszystko o całej sieci (tzn. otrzyma wszystkie pakiety LSA).
3. **Tworzenie bazy stanów łączy (LSDB)**
   >Gdy już każdy wie jak wygląda cała sieć, można utworzyć tablicę topologii zgodną z treścią wszystkich LSA razem. W bazie tablicy topologii (LSDB) są wszystkie informacje o topologii sieci.
4. **Wykonanie algorytmu SPF**
   >Oblicza on drzewa SPF zawierające trasy do różnych punktów w sieci.
5. **Wybór najlepszej trasy**
   >Ze wszystkich gałęzi drzewa wybierane są te o najniższym koście, są one ostatecznie wpisywane do tablicy routingu.
   
Podczas uzyskiwania zbieżności router przechodzi przez [[stany operacyjne OSPF]] w zależności od etapu i typu sieci.