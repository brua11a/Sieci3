### Odwrotność normalnej maski sieci.
#### 0 -> dopasowanie
#### 1 -> ignoruj

Maska blankietowa składająca się z samych zer (`0.0.0.0`) oznacza dokładne dopasowanie, czyli adres hosta. **Zamiast używania jej można użyć słowa kluczowego `host`.**

Maska blankietowa odpowiadająca zakresowi podsieci IPv4 (np. `0.0.0.255` dla podsieci `/24`) może zezwolić na wszystkie hosty w podsieci.

Maska blankietowa odpowiadająca zakresowi innych adresów IPv4 (np. `0.0.15.255` dla podsieci `/24`) może zezwolić na ruch z kilku podsieci.

Maska blankietowa składająca się z samych jedynek (`255.255.255.255`) oznacza dopasowanie do każdego. **Zamiast jej używania można użyć słowa kluczowego `any.`**



![[Pasted image 20250507000612.png]]![[Pasted image 20250509153001.png]]
