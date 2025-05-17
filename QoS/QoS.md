**QoS** (*Quality of Service*) pozwala na zapewnienie priorytetu ruchowi wrażliwemu na opóźnienia, takiemu jak głos czy video. Ruch, który nie wymaga płynności i może sobie pozwalać na opóźnienia zostaje wtedy z tyłu.

![[Pasted image 20250517165143.png]]

Opóźnienia mogą być spowodowane wieloma czynnikami, najczęściej jest to agregacja wielu łączy wejściowych do jednego wyjściowego lub przejście z większej do mniejszej prędkości. W sytuacji, w której dojdzie do zatoru w sieci i ruch musi oczekiwać w kolejce, grozi nam, że pamięć routera się zapełni i wszystkie nowe pakiety zostaną odrzucone i utracone. QoS pozwala jednak [[Kolejkowanie QoS|kolejkować]] różne typy ruchu osobno na podstawie priorytetu.

![[Pasted image 20250517164005.png]]

Jednym z mechanizmów "ratowania" ruchu jest bufor opóźnienia, który kolejkuje pakiety by kompensować napotkany [[jitter]] poprzez buforowanie pakietów po czym wysłanie ich w strumieniu już bez jittera. 