**Lista ACL** (*Access Control List*) to seria instrukcji (ACE - *Access Control Entry*) używanych do filtrowania pakietów na podstawie informacji znajdujących się w pakiecie - adresu IP i numeru portu. Filtrowanie odbywa się na warstwie 3 (sieci) i 4 (transportowej).

Jeśli wdrożymy ACL na interface to KAŻDY pakiet przed przejściem przez niego zostanie sprawdzony wg. zasad określonych na ACL.

ACL pozwalają chociażby ograniczyć ruch niepożądany, np. odfiltrować usługi, których nie przewiduje polityka firmy, a także zwiększyć zabezpieczenia poprzez ograniczenie dostępu do konkretnych hostów. W połączeniu z [[QoS]] pozwala także na zapewnienie priorytetu konkretnym typom ruchu

Ważne jest to, że zasady ACE są czytane **"od góry do dołu"**, czyli jeśli jakaś zasada "wyżej" w liście dotyczy pakietu to nie są czytane już te "niżej". Na samym "dole" każdej listy ACL istnieje niewidzialne `deny any` - czyli ruch, na który nie zezwalamy jasno i wyraźnie zostaje odrzucany.
##### Obsługiwane są dwa typy list ACL:
1. [[Standardowe ACL]]
   >Filtruje na podstawie TYLKO źródłowego adresu IPv4.
2. [[Rozszerzone ACL]]
   >Filtruje na podstawie źródłowego i docelowego adresu IPv4, a także konkretnego protokołu.
   
ACL mogą dotyczyć ruchu **PRZYCHODZĄCEGO** i **WYCHODZĄCEGO**, to i to ma **osobne** zasady, które należy osobno skonfigurować jeśli pojawi się taka potrzeba.

![[Pasted image 20250509151819.png]]
##### Można (ale nie trzeba zawsze) skonfigurować 4 ACL na jednym routerze:
- wchodzący IPv4
- wychodzący IPv4
- wchodzący IPv6
- wychodzący IPv6

Pakiety filtrujemy na **WEJŚCIU** zazwyczaj gdy sieć dołączona do interfejsu wyjściowego jest jedynym źródłem informacji - czyli cały ruch do przefiltrowania wchodzi jednym interfejsem, zatem można go odfiltrować zanim przejdzie do interfejsu wyjściowego, co jest "lżejsze" dla routera niż przeniesienie pakietu na interfejs wyjściowy i dopiero wtedy go odfiltrowanie.

Pakiety są traktowane jako "wychodzące" po wykonanym procesie routingu ale przed wysłaniem ruchu sieciowego dalej (czyli po routingu wewnętrznie ale przed wysłaniem do np. innego routera czy switcha). Filtrujemy na **WYJŚCIU** gdy tych samych zasad filtrowania chcemy użyć do ruchu pochodzącego z wielu interfejsów wejściowych - wtedy zamiast ustawiać zasad na każdym interfejsie wejściowym osobno można to po prostu zrobić na wyjściu.