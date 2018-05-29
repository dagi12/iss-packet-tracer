# Rozwiązania Ćw1

## Zadanie 1

### Czym różni się adres MAC od adresu IP

- Adres mac jest adresem przypisanym przez producenta urządzenia sieciowego jako swoisty unikalny identyfikator urządzenia. 
-Adres IP jest przydzialny przez Router lub ogólniej konfigurację danej sieci służy do odnajdowania się użądzęń w protokole TCP/IP.


### Czym się różnią hub, switch i router

- Hub to proste urządzenie działające w warstwie dostępu do sieci. Przekazuj sygnał wejściowy na wszystkie wyjściowy bez modyfikacji.
- Switch przekazuje pakiety pomiędzy urządzeniami sieci lokaljnej, buforuje przesyłane dane oraz sprawdza ich poprawnośc switche mogą być zarządzalne
- Router to zaawansowane urządzenie w sieci. Służące do komunikacji pomiędzy różnymi sieciami. Router jest miejscem, w którym. Sieć internetowa jest oparta na efektywnej komunikacji pomiędzy routerami. Router posiada adres IP w każdej sieci do której jest podłączony

#### Która warstwa w modelu TCP/IP odpowiada za konwersję danych na sygnały elektryczne

- w warstwie dostępu do sieci

### W której warstwie modelu TCP/IP zachodzi routing,

- w warstwie internetu

### W jakiej kolejności kapsułkowane są dane przy transmisji w sieci TCP/IP (wybierz jedno):
- []dane, ramka, pakiet, segment, bity,
- [] segment, dane, pakiet, ramka, bity,
- [x] dane, segment, pakiet, ramka, bity,
- [] dane, segment, ramka, pakiet, bity.

## Zadanie 2
Wypisz adres sieci, maskę i zakres adresów jakie można przypisać komputerom w następujących podsieciach:

### 10.0.0.0/8
Adres: 10
Maska: 255.0.0.0
Zakres 0.0.1 - 255.255.254
### 172.16.0.0/25
Adres: 172.16.0
Maska: 255.255.255.128
Zakres 129-254
### 2001:808:114:2::/64
Adres: 2001:808
Maska: 2001:2001:0:0
Zakres 0000:0001 - 2001:2000

## Zadanie 3
### Czy z sieci 10.0.0.0/16 da się wydzielić 17 sieci mieszczących po 120 komputerów. Jeżeli tak to zaproponuj podział sieci na podsieci minimalizując użycie adresów.

Tak
Zakres sieci 10.0.x.x do 10.16.x.x
Zakres komputerów 10.x.0.1 10.x.0.120

## Zadanie 4
### Jeżeli do huba podłączone są trzy komputery to ile istnieje domen kolizyjnych, a ile domen rozgłoszeniowych w tej sieci. Jak sytuacja zmieni się po zastąpieniu huba switchem (bez skonfigurowanych VLANów)?

1. Przypadek
- domen kolizyjnych - 1
- domen rozgłoszeniowych 1
2. Przypadek
- domen kolizyjnych - 3
- domen rozgłoszeniowych - 1

## Zadanie 5
## Na poniższym rysunku przedstawiony jest schemat sieci: 
![alt text](https://eduwiki.wmi.amu.edu.pl/ruanda/DISS/Cw1?action=AttachFile&do=get&target=zad5.png)
## Komputer A wysyła dane do komputera B. Jakie adresy fizyczne i logiczne będą użyte we wszystkich ramkach powstałych w czasie tej komunikacji.

Komputer A użyje adresu fizycznego Komputera B i wyśle pakiet bezpośrednio do niego ponieważ adres IP sugeruje tą samą sieć.

Zadanie 6
# Na poniższym rysunku przedstawiony jest schemat sieci:
![alt text](https://eduwiki.wmi.amu.edu.pl/ruanda/DISS/Cw1?action=AttachFile&do=get&target=zad6.png)

## Komputer A wysyła dane do komputera B. Jakie adresy fizyczne i logiczne będą użyte we wszystkich ramkach powstałych w czasie tej komunikacji.

Komputer A wyślę ramkę do adresu fizycznego bramy (routera) czyli 00:16:3E:00:00:42, z informacją, że docelowy adres danych to 10.0.1.2, router zestripuje informację o swoim adresie fizycznym, a następnie przetłumaczy docelowy adres logiczny 10.0.1.2 na adres fizyczny Komputera B i wyślę do niego ramkę z danymi. 

#Zadanie 7
##Korzystając z rysunku do zadania 6 opisz tablice routingu we wszystkich urządzeniach tak aby komunikacja między nimi była możliwa. Każdy wpis dla tablicy routingu powinien zawierać: adres sieci docelowej,bramę lub interfejs (załóżmy, że interfejsy komputerów nazywają się "eth0")
10.0.0.0 255.255.255.0 eth1/1
10.0.1.0 255.255.255.0 eht1/2
# Zadanie 8
## Na poniższym rysunku przedstawiony jest schemat sieci:
![alt text](https://eduwiki.wmi.amu.edu.pl/ruanda/DISS/Cw1?action=AttachFile&do=get&target=zad8.png)

# Komunikacja między komputerami A i B nie działa. Jakie mogą być przyczyny problemu? Zaproponuj rozwiązanie problemu.
Możliwe, żw wiadomośc krąży w pętli i nie może dotrzeć do celu. Należy zastować protokół Spanning Tree i wyłączyć niepotrzebne połączenia.

# Rozwiązania Ćw2 