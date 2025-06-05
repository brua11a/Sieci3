#### Dokumentacja sieci zazwyczaj opiera się na:
1. **Diagramie fizycznym i logicznym topologii**
   >Topologia fizyczna to fizyczny układ urządzeń podłączonych do sieci, czyli jej rzeczywiste fizyczne elementy. Znajdują się tam informacje takie jak nazwy urządzeń, ich rozłożenie, używane interfejsy i kable.
   >
   >Topologia logiczna opisuje to, jak są przekazywane dane w sieci podczas komunikacji. Połączenia pomiędzy różnymi segmentami sieci nie muszą odpowiadać fizycznym lokalizacjom. Znajdują się tam informacje takie jak adresy IP, routing, informacje warstwy 2 (VLAN, trunk, EtherChannel)
2. **Dokumentacji urządzeń sieciowych - wszystkie ważne parametry**
   >Dla routera:
   >![[Pasted image 20250530111251.png]]
   >
   >Dla switcha:
   >![[Pasted image 20250530111333.png]]
3. **Dokumentacji bazowej (*baseline*) wydajności sieci, stanu odniesienia**
   >Ma na celu wyznaczenie *normalnej* wydajności sieci, czyli czego możemy od niej się spodziewać i oczekiwać, a jakie sytuacje można uznać za *nienormalne*. Wymaga to zebrania informacji o wydajności poszczególnych portów i urządzeń. Bez stanu odniesienia nie da się stwierdzić czy chociażby sieć jest wystarczająco wydajna na wyznaczone potrzeby.
   >
   >W procesie dokumentacji mogą wyjść różne niedociągnięcia w sieci, zatory lub niewykorzystane łącza. Dzięki temu można przeprojektować sieć. Pomiar stanu odniesienia pozwala też ocenić trafnie zmiany w wydajności po dokonaniu zmiany w sieci.
   >
   >Warto jest zacząć od badania kluczowych urządzeń w sieci, na przykład serwerów. Wymagana jest tutaj topologia logiczna.
   >
   >Stan odniesienia sieci powinien odpowiadać na następujące pytania:
>- Jak sieć funkcjonuje podczas normalnego lub typowego dnia?
>- Gdzie może wystąpić najwięcej błędów?
>- Która część sieci jest najintensywniej wykorzystywana?
>- Która część sieci jest najmniej wykorzystywana?
>- Jakie urządzenia należy monitorować i jakie progi alarmowe należy ustawić?
>- Czy sieć może spełniać określone zasady?