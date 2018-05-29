# ISS notatki

# Sieci - wstęp

## Czym jest sieć komputerowa?
- śleć to zbiór komputerów urządzeń połączonych ze sobą w celu wymiany informacji
- informacje wymieniane są przez programy
- pojęcie komputera urządzenia jest nieprecyzyjne
    - w dalszym ciągu będą używane określenia "host i urządzenie"

## Model warstwowy sieci
- komunikacja podzielona jest na warstwy w celu uproszczenia implementacji
- sieć TCP/IP podzielona jest na cztery warstwy:
    - warstwa dostępu do sieci — ang- link layer
    - warstwa internetu — ang- internet layer
    - warstwa transportowa— ang- transport layer
    - warstwa aplikacji — ang- application layer

## Warstwa dostępu do sieci
- najniższa warstwa
- odpowiada za bezpośrednią komunikację między hostami
- lokalne sieci najczęściej oparte są o technologię ethernet, która określa specyfikację przewodów, przesyłanych sygnałów oraz format ramek i protokołów niższych warstw

## Ethernet

### Ethernet — warstwa fizyczna
- ethernet ewoluuje przez co dostępnych jest wiele wersji
- współczesny ethernet działa przy użyciu skrętki lub światłowodów
    - skrętka jest tanim i odpornym rozwiązaniem,ale ogranicza zasięg do 1ooM
    - światłowód ma zasięg
- dostępne przepustowości (najczęściej): 100Mb/s, 1Gb/s, 10Gb/s, 40Gb/s

### Ethernet — ramka
- każda ramka zaczyna się preambułą (siedem bajtów o wartości 10101010) i polem startu (bajt o wartości 10101011)
- następnie przesyłany jest nagłówek
- 6 bajtów adresu docelowego i 6 bajtów adresu źródłowego (mac)
- 2 bajtów typu lub długości ramki
- następnie przesyłane są właściwe dane (max 1500 bajtów)
- ramka kończy się 4 bajtami sumy kontrolnej (obejmującej nagłówek i dane) oraz 12 bajtami przerwy między pakietami (bajty o wartości 0)

### Ethernet — warstwa łącza danych
- ethernet określa sposób interpretacji sygnału w medium
- dane między komputera wymieniane są w ramkach

### Ethernet — urządzenia
- dawniej powszechne było użycie hubów, urządzeń pracujących w pierwszej warstwie i przesyłających sygnały elektryczne z jednego portu na wszystkie
- najczęściej używanymi współcześnie urządzeniami są switche, urządzenia pracujące w drugiej warstwie
- switch tworzy niezależne połączenie do każdego hosta, buforuje przesyłane dane oraz sprawdza ich poprawność
- switch przesyła otrzymane ramki do odpowiedniego portu (w miarę możliwości)
- switche mogą być zarządzalne

### Ethernet — komunikacja
- każde urządzenie komunikujące się w sieci ethernet ma adres mac (48-bitowa liczba) przypisany przez producenta
- domena kolizyjna to fizyczny fragment sieci, w którym współdzielone jest medium, więc podłączone urządzenia mogą zakłócać swoją pracę
- domena rozgłoszeniowa to logiczny segment sieci, w którym komunikacja przebiega bezpośrednio
- hosty podłączone do różnych domen rozgłoszeniowych muszą skorzystać z wyższych warstw aby się ze sobą komunikować
- domena rozgłoszeniowa może powstać przez fizyczne wydzielenie fragmentu sieci lub wykorzystanie wirtualnej sieci lokalnej, tzw. VLAN

### Ethernet — VLAN
- VLAN to logicznie wydzielona sieć w ramach większej sieci fizycznej
- do utworzenia VLANu niezbędne jest użycie zarządzalnego przełącznika, który pozwala przypisać port do VLANu
- port może przesyłać ruch z wielu VLANów, każdy jest określony przez numer VLANu (id)
- ramki przesyłane przez taki port są dłuższe o 4 bajty (umieszczone po adresie źródłowym) z czego na zapis id przeznaczone jest 12 bitów (wartości 0-4094)

### Ethernet — spanning tree
- istotną kwestią w sieciach ethernet jest unikanie pętli
- pętle mogą powstać przez błąd w połączeniu lub konfiguracji urządzeń
- pętle mogą być tworzone celowo w celu zwiększenia dostępności sieci
- w każdym przypadku konieczne jest wdrożenie stp w celu eliminacji pętli przez wyłączenie nadmiarowych połączeń

### Ethernet — agregacja łączy
- agregacja łączy umożliwia wykorzystanie wielu równoległych łączy fizycznych jako jedno łącze logiczne
- takie połączenia korzystają z protokołu lacp służący do negocjacji i aktywnego monitorowania zagregowanych łączy
- równoległe połączenia fizycznie tworzą pętlę, ale ponieważ logicznie są jednym połączeniem to działają równocześnie

### Czy wyższe warstwy są potrzebne?
- hosty mogą komunikować się wyłącznie w ramach domeny rozgłoszeniowej
- problemy
    - broadcast
    - medium

### Warstwa internetu
- warstwa internetu zapewnia transmisję przez jedną lub więcej sieci
- przesyłanie danych między sieciami nazywa się routingiem
- w modelu TCP/IP warstwę internetu obsługuje protokół IP
- obecnie działają dwie wersje protokołu IP: IPv4 i IPv6
- dane w protokole IP przesyłane są w pakietach

### IPv4
- protokół IPv4 stosuje 32-bitowe adresy, zapisywane jako 4 oktety w postaci dziesiętnej rozdzielone znakiem np- 150.254.78.2
- teoretycznie możliwe jest zaadresowanie ponad 4 miliardów hostów
- w praktyce duża część adresów IPv4 jest zarezerwowana (18 milionów adresów prywatnych, 270 milionów adresów multicast)

### IPv6
- IPv6 rozwiązuje problem zbyt małej przestrzeni adresowej protokołu IPv4
- protokół IPv6 stosuje 128-bitowe adresy, zapisywane jako oktety w postaci szesnastkowej rozdzielone co cztery bajty znakiem ":" np. 2001:808:114:2::2
- IPv6 nie jest tylko większą wersją IPv4

### IP - nagłówek
- istotne pola nagłówka IP (niezależnie od wersji) to:
    - typ pakietu, określający wersję protokołu
    - ttl
    - typ przesyłanych danych
    - adresy żródłowy i docelowy
- nagłówek IPv6 jest uproszczony o elementy, które w praktyce okazały się nieprzydatne, np. fragmentację pakietów lub sumę kontrolną

### IP — adresy
- hosty muszą posiadać unikalne adresy
- aby zagwarantować unikalność adresów, każda sieć powinna korzystać z
adresów przydzielanych przez RIR (ang- regional internet registry)
- cała przestrzeń adresowa podzielona jest na mniejsze sieci zgodnie z metodą CIDR

### CIDR
- każda sieć opisana jest przez adres sieci oraz maskę
- maska opisuje ile bitów adresu, zaczynając od najbardziej znaczącego bitu, stanowi adres sieci
- pozostałe bity służą do adresacji hostów
- pierwszy adres (z wyzerowanymi bitami hosta) jest zarezerwowany jako adres sieci
- ostatni adres w sieci IPv4 ma specjalne znaczenie
- maskę sieci podaje się w postaci prefiksu, czyli liczby bitów

### Cidr — przykład
- adres 192.0.2.0/24 oznacza, że adres sieci składa się z 24 bitów, natomiast pozostałe 8 bitów stanowi adres hosta w tej sieci
- jeżeli przepiszemy pierwsze 24 bity adresu sieci a w następnych 8 bitach wpiszemy wartości to otrzymamy adres 192.0.2.1 jako pierwszy adres hosta
- jeżeli w 8 bitach hosta wpisujemy maksymalną wartości (1 1 1 1 1 1 1 1) to otrzymamy adres 192.0.2.255 jako adres rozgłoszeniowy
- ostatni adres hosta to 192.0.2.254
- maskę można alternatywnie zapisać jako 255.255.255.0 (24 starsze bity ustawione)

### IP — komunikacja
- komunikacja między dwoma hostami znajdującymi się w tej samej sieci zachodzi bezpośrednio
- adresy IP mapowane są za pomocą protokołu ARP (dla IPv4) lub NDP (dla IPv) na adresy warstwy sieci

### IP — komunikacja
- komunikacja między różnymi sieciami zapewniona jest przez routery
- w najprostszej strukturze router to urządzenie posiadające interfejs w każdej sieci z adresem IP przypisanym do tej sieci
- hosty mogą komunikować się bezpośrednio z innymi hostami w tej samej sieci oraz routerem
- pakiety adresowane do hostów w danej sieci są przesyłane do routera, który następnie przesyła je do właściwego komputera w innej sieci

### IP — routing
- każdy host i router zawiera tablicę routingu
- tablica routingu określa co zrobić z pakietem na podstawie adresu docelowego
- wpis w tablicy routingu zawiera adres sieci z maską i bramę
- dla uproszczenia tablic stosuje się bramę domyślną
- hosty mają przeważnie dwa wpisy w tablicy routingu: lokalną sieć i bramę domyślną
- routery mają bardziej skomplikowane trasy

### Czy wyższe warstwy są potrzebne
- hosty mogą wysyłać proste datagramy
- problemy:
    - jak zapewnić niezawodność komunikacji
    - jak zagwarantować dotarcie pakietów w odpowiedniej kolejności
    - w jaki sposób host ma wiedzieć, który program wysyła pakiet

### Warstwa transportowa
- istnieje wiele protokołów warstwy transportowej
- najważniejsze są dwa z nich: TCP i UDP

## TCP

### TCP - 1
- podstawowy protokół warstwy transportowej
- zapewnia niezawodne połączenie między dwoma punktami z zachowaniem kolejności przesyłanych danych oraz wykrywaniem błędów
- z punktu widzenia aplikacji połączenie TCP jest strumieniem oktetów

### TCP - 2
- dane w protokole TCP są przesyłane w segmentach
- nagłówek TCP zawiera m.in.
    - port nadawcy i odbiorcy (16-bitowe)
    - numery sekwencyjne potwierdzenia (32-bitowe)
    - flagi
    - sumę kontrolną

### TCP — komunikacja
- port źródłowy i docelowy pozwalają hostom określić jaki program odpowiada za dany segment
- w TCP przed transmisją właściwych danych konieczne jest nawiązanie połączenia, tzw. three—way handshake

### TCP — nawiązywanie połączenia
- strona inicjująca połączenie (klient) wysyła do serwera segment z ustawioną flagą SYN oraz początkowym numerem transmisji
- w odpowiedzi klient otrzymuje potwierdzenie otrzymania segmentu przez ustawioną flagę ACK i numeru potwierdzenia (numer sekwencji jaki serwer spodziewa się otrzymało) oraz flagę syn z początkowym numerem sekwencji transmisji od serwera
- nawiązywanie połączenia kończy się odesłaniem potwierdzenia otrzymania segmentu przez klienta z ustawioną flagą ACK oraz numerem potwierdzenia

### TCP — cechy niepożądane (czasem)
- w pewnych zastosowaniach cechy protokołu TCP są niepożądane, np. gry czasu rzeczywistego lub połączenia głosowe, gdzie ważniejsze jest odebranie większości danych bez opóźnień niż wszystkich danych w prawidłowej kolejności
- wymiana prostej informacji wymaga przesłania wielu pakietów w celu inicjacji zakończenia połączenia

### UDP
- UDP jest prostym protokołem bezpołączeniowym
- w nagłówku określone są jedynie porty nadawcy i odbiorcy (wartości 16—bitowe), długości oraz suma kontrolna (obowiązkowa dla IPv4)

### Czy wyższe warstwy są potrzebne
- dzięki TCP i UDP programy mogą się ze sobą komunikować
- problemy:
    - programy muszą wiedzieć jak się ze sobą komunikować
    - protokoły niższych warstw zapewniają jedynie komunikację, wszystkie urządzenia i hosty muszą być odpowiednio skonfigurowane, a użytkownik znać stertę nic nie mówiących numerów IP i portów

### Warstwa aplikacji
- warstwa aplikacji składa się z 2 typów protokołów:
    - użytkownika
    - wspomagających
- protokoły wspomagające

# Tworzenie podsieci (subnetting)

- problematyka
    - sieć IP powstała aby połączyć wiele niezależnych sieci (stąd nazwa - internet)
    - każda z sieci składowych może używać różnych technologii warstwy dostępu do
danych, np- ethernet, dsl, które nie są ze sobą kompatybilne
~ komunikację między sieciami zapewniają routery, urządzenia warstwy internetu
podłączone ze sobą oraz sieciami, które spinają w siec- internet
- routery nie muszą być połączone bezpośrednio
~ jeżeli struktura połączeń między routerami może mieć (| ma] cykle, oraz
odległości większe niż 2 to w jaki sposób router ma zdecydować o pakietach
zaadresowanych do hostów podłączonych bezpośrednio?
rozwiązanie
- każdy router ma tablice routingu, które mówią co zrobić z pakietami na podstawie adresu
docelowego, który zawierają
~ tablice routingu nie mogą zawierać informacji o każdym adresie IP
- takie tablice byłyby bardzo duże
- wszelkie zmiany wymagałyby rekonfiguracji wszystkich! routerów
- adresy IP są pogrupowane w zakresy adresów
- w tablicach routingu znajdują się informacje co zrobić z pakietami na podstawie przynależności
danego adresu do grupy
- administrator może w lokalnej sieci podzielić z "swój" zakres adresów na jeszcze mniejsze
fragmenty, wystarczy, że wie o tym lokalny router
- każda grupa adresów tworzy podsieć
tworzenie podsieci (subnet i'ing)
- tworzenie podsieci to proces, w którym sieć IP dzieli się na mniejsze sieci-
- tworzenie podsieci dotyczy sieci IPv4 i IPv6-
- zakresy adresów IP nie mogą być dowolne
- muszą być jednoznaczne
- nie mogą na siebie nachodzić
- muszą być przyjazne dla routerów
adres IPv4
~ adres IPv4 jest 32-bitową liczbą całkowitą, w systemie dziesiętnym może
przyjmować wartości od 0 do 4 294 967 296
~ tradycyjnie adresy IPv4 zapisuje się jako ciąg 4 8-bitowych liczb oddzielonych
kropkami, w tym formacie mogą przyjmować wartości od 00-00 do
255-255-255-255
- komputery rozumieją wyłącznie wartości binarne, w tym formacie adresy IPv4
mogą przyjmować wartości od 00000000 00000000 00000000 00000000 do
11111111 11111111 11111111 11111111
podsieci IPv4
- podsiec IPv4 powstaje przez podzielenie binarnego zapisu adresu IP na część sieć! i
część hosta
- podsieć można dzielić na kolejne podsieci, przez podział części hosta na częśc
sieci i część hosta
- bity na część sieci zawsze są najstarszymi bitami
- liczba bitów części sieci nazywa się maska sieci
- zakres adresów w danej sieci określa się adresem sieć! i maską
- adres sieci to adres, który wszystkie bity części hosta ma- wyzerowane
maska sieci - uwagi
- maskę zapisuje się jako prefiks (np- /2ó) czyli liczbę bitów części sieci
- taki zapis maski nie jest przyjazny dla procesora
- wewnętrznie maska zapisana jest jako liczba 32—bitowa, gdzie bity części sieci są
ustawione, natomiast bity części hosta są wyzerowane
› tak zapisaną maskę można zapisac jak adres IPv4, np- 255-255-255-192
- taki zapis maski nie jest przyjazny dla ludzi, ale wiele systemów nadal go używa
podsieć - użycie
- aby podsieć "działała" każdy komputer w sieci powinien! znać swój adres (z zakresu
adresów podsieci) oraz maskę używaną w sieci
- w ten sposób komputer wie, które adresy są lokalnie w sieci, a które dostępne
przez router
- router też ma przypisany adres z zakresu adresów podsieci i zna maskę sieci
IPv6
- zasady są analogiczne jak dla IPv4, tylko adresy mają 128 bitów i zapisuje się je
w inny sposób:
adresy IPv6 zapisuje się w systemie szesnastkowym, w grupach 4—cyfrowych
(o-f] oddzielonych znakiem
każda grupa opisuje 16 bitów adresu (jest 8 grup]
każda cyfra opisuje 4 bity adresu
maski mogą być teoretycznie dowolne, ale stosuje się wielokrotności 4
najmniejsza sieć, której nie powinno się już dzielić (choć można) to /64
specjalne sieci IPv4 (rfc 3330)
- loopback 127-0-0-0/8
- sieci prywatne: 10-0-0-0/8, 172-16-0-0/12,192-168-0-0/1ó
- link—localz 169-254-0-0/1ó
- multicast:224-0-0-0/4
~ zarezerwowane:240-0-0-0/4
specjalne sieci IP (rfc 5156)
- loopback: ::1/128, nieokreślony adres: ::/128
- link—local: fe80::/10
