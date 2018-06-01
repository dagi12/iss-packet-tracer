
# Tworzenie podsieci (subnetting)

## Problematyka
- sieć IP powstała aby połączyć wiele niezależnych sieci (stąd nazwa - internet)
- każda z sieci składowych może używać różnych technologii warstwy dostępu do danych, np- ethernet, dsl, które nie są ze sobą kompatybilne
- komunikację między sieciami zapewniają routery, urządzenia warstwy internetu podłączone ze sobą oraz sieciami, które spinają w siec- internet
- routery nie muszą być połączone bezpośrednio
- jeżeli struktura połączeń między routerami może mieć (i ma) cykle, oraz odległości większe niż 2 to w jaki sposób router ma zdecydować o pakietach zaadresowanych do hostów niepodłączonych bezpośrednio?

## Rozwiązanie
- każdy router ma tablice routingu, które mówią co zrobić z pakietami na podstawie adresu docelowego, który zawierają
- tablice routingu nie mogą zawierać informacji o każdym adresie IP
    - takie tablice byłyby bardzo duże
    - wszelkie zmiany wymagałyby rekonfiguracji wszystkich routerów
- adresy IP są pogrupowane w zakresy adresów
    - w tablicach routingu znajdują się informacje co zrobić z pakietami na podstawie przynależności danego adresu do grupy
    - administrator może w lokalnej sieci podzielić z "swój" zakres adresów na jeszcze mniejsze fragmenty, wystarczy, że wie o tym lokalny router
    - każda grupa adresów tworzy podsieć
    
## Tworzenie podsieci (subnetting)
- tworzenie podsieci to proces, w którym sieć IP dzieli się na mniejsze sieci
- tworzenie podsieci dotyczy sieci IPv4 i IPv6
- zakresy adresów IP nie mogą być dowolne
    - muszą być jednoznaczne
    - nie mogą na siebie nachodzić
    - muszą być przyjazne dla routerów

## Adres IPv4
- adres IPv4 jest 32-bitową liczbą całkowitą, w systemie dziesiętnym może przyjmować wartości od 0 do 4 294 967 296
- tradycyjnie adresy IPv4 zapisuje się jako ciąg 4 8-bitowych liczb oddzielonych kropkami, w tym formacie mogą przyjmować wartości od 0.0.0.0 do 255.255.255.255
- komputery rozumieją wyłącznie wartości binarne, w tym formacie adresy IPv4 mogą przyjmować wartości od 00000000 00000000 00000000 00000000 do 11111111 11111111 11111111 11111111

## Podsieć IPv4
- podsieć IPv4 powstaje przez podzielenie binarnego zapisu adresu IP na część sieci i część hosta
- podsieć można dzielić na kolejne podsieci, przez podział części hosta na część sieci i część hosta
- bity na część sieci zawsze są najstarszymi bitami
- liczba bitów części sieci nazywa się maska sieci
- zakres adresów w danej sieci określa się adresem sieci i maską
    - adres sieci to adres, który wszystkie bity części hosta ma wyzerowane

## Maska sieci - uwagi
- maskę zapisuje się jako prefiks (np. /2ó) czyli liczbę bitów części sieci
- taki zapis maski nie jest przyjazny dla procesora
- wewnętrznie maska zapisana jest jako liczba 32—bitowa, gdzie bity części sieci są ustawione, natomiast bity części hosta są wyzerowane
- tak zapisaną maskę można zapisać jak adres IPv4, np. 255.255.255.192
- taki zapis maski nie jest przyjazny dla ludzi, ale wiele systemów nadal go używa

## Podsieć - użycie
- aby podsieć "działała" każdy komputer w sieci powinien znać swój adres (z zakresu adresów podsieci) oraz maskę używaną w sieci
- w ten sposób komputer wie, które adresy są lokalnie w sieci, a które dostępne przez router
- router też ma przypisany adres z zakresu adresów podsieci i zna maskę sieci 

## IPv6
- zasady są analogiczne jak dla IPv4, tylko adresy mają 128 bitów i zapisuje się je w inny sposób:
    - adresy IPv6 zapisuje się w systemie szesnastkowym, w grupach 4—cyfrowych (0-F) oddzielonych znakiem ":"
    - każda grupa opisuje 16 bitów adresu (jest 8 grup]
    - każda cyfra opisuje 4 bity adresu
    - maski mogą być teoretycznie dowolne, ale stosuje się wielokrotności 4
    - najmniejsza sieć, której nie powinno się już dzielić (choć można) to /64

## Specja;lne sieci IPv4 (RFC3330)
- loopback 127.0.0.0/8
- sieci prywatne: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/1ó
- link—local: 169.254.0.0/16
- multicast: 224.0.0.0/4
- zarezerwowane: 240.0.0.0/4

## Specjalne sieci IP (RFC5156)
- loopback: ::1/128, nieokreślony adres: ::/128
- link—local: FE80::/10