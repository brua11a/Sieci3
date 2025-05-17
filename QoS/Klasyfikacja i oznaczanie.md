Klasyfikacja i oznaczenie są konieczne przed wdrożeniem [[QoS]]. Dzięki temu określana jest klasa ruchu znajdującego się w pakietach i ramkach. Do klasyfikacji może służyć interfejs, [[Lista ACL|lista ACL]], mapa klas, NBAR (*Network Based Application Recognition*)...

Oznakowanie wiąże się z dopisaniem jakiejś wartości do nagłówka pakietu. Zostaje on sprawdzony przez urządzenie w celach weryfikacji. Są różne sposoby oznakowania ruchu, nie ma tutaj jednego standardu. Należy też zastanowić się kiedy oznaczyć ramki a kiedy pakiety. Można posłużyć się tymi zasadami:
- Oznaczanie ramek w warstwie 2 może być wykonywane dla ruchu innego niż IP.
- Oznaczanie ramek w warstwie 2 jest jedyną opcją QoS dostępną dla przełączników, które nie są „świadome IP”.
- Oznakowanie warstwy 3 będzie zawierało informacje QoS od początku do końca.

![[Pasted image 20250517175331.png]]

Na przykład dla Ethernetu do ramki są dodawane dwa pola po polu adresu źródłowego MAC - TPID i TCI. W nich znajduje się 3b pole PRI odpowiadające klasie usług CoS. Może reprezentować następujace wartości:

![[Pasted image 20250517175430.png]]

W pakietach IPv4 i IPv6 są przewidziane pola na priorytet, konkretnie ToS (*Type of Service* dla IPv4) i TC (*Traffic Class* dla IPv6). Kiedyś za poziom QoS odpowiadał IPP, ale teraz przestawiono się na 6B DSCP żeby móc dokładniej sklasyfikować ruch. 

Jeśli DSCP=0, to mowa o [[Modele QoS|best-effort]], jeśli DSCP=46 to używany jest EF (*Expedited Forwarding*)m który jest używany tylko do klasyfikacji głosu. Najbardziej rozbudowany jest AF (*Assured Forwarding*), w którym 5 pierwszych bitów wskazuje kolejkę i preferencję upuszczania.

![[Pasted image 20250517180225.png]]