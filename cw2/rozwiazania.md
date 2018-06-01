# Zadanie 1 Wyjasnij:
## jakie są korzyści z podziału sieci na mniejsze sieci
- wydajność - pakiety rozgłoszeniowy nie muszą dochodzić do wszystkich urządzęń, a tylko do tych w podsieco
- zmniejszenie przeciążenia - tworzenie podsieci pozwala na zredukowanie obciążenia, odpowiednio zoptymalizowana podsieć zapewnia, że pakiety urządzeń, które najczęściej się ze sobą komunikują zostają w danej podsieci
- zwiększenie bezpieczeństwa - jeżeli jakaś część naszej sieci została przejęta lub zainfekowana w stosunkowo prosty sposób możemy odłączyć podsieć z użytku by nie zagrozić reszcie sieci

## jakie rozmiary mogą mieć sieci IP (czy liczba adresów w danej sieci może być dowolna, np. czy można utworzyć sieć, która ma dokładnie 42 adresy)

- nie, ilość dostępnych sieci to jest (potęga liczby 2 odjąć 2)

## jaka jest rola maski sieci

- rolą maski jest wskazanie, które adresy są dostępne lokalnie, a które są dostępne przez router

##  ile adresów dowolnej podsieci (opisanej prefiksem /N) można wykorzystać na adresację hostów

(2 ^ (32 - N))

# Zadanie 2 Uzupełnij poniższą tabelę:

| Prefiks | Maska sieci     | Liczba adresów hostów w podsieci |
|---------|-----------------|----------------------------------|
| /16     | 255.255.0.0     | 65,536                           |
| /17     | 255.255.128.0   | 32,768                           |
| /18     | 255.255.192.0   | 16,384                           |
| /19     | 255.255.224.0   | 8,192                            |
| /20     | 255.255.240.0   | 4,096                            |
| /21     | 255.255.248.0   | 2,048                            |
| /22     | 255.255.252.0   | 1,024                            |
| /23     | 255.255.254.0   | 512                              |
| /24     | 255.255.255.0   | 256                              |
| /25     | 255.255.255.128 | 128                              |
| /26     | 255.255.255.192 | 64                               |
| /27     | 255.255.255.224 | 32                               |
| /28     | 255.255.255.240 | 16                               |
| /29     | 255.255.255.248 | 8                                |
| /30     | 255.255.255.252 | 4                                |

# Zadanie 3 Uzupełnij poniższą tabelę:


| Adres IP          | Maska sieci     | Adres sieci    | Liczba hostów w podsieci | Broadcast      |
|-------------------|-----------------|----------------|--------------------------|----------------|
| 10.25.66.154/23   | 255.255.254.0   | 10.25.66.154   | 512                      | 10.25.66.255   |
| 192.168.20.123/28 | 255.255.255.240 | 192.168.20.112 | 16                       | 192.168.20.127 |
| 63.24.89.21/18    | 255.255.192.0   | 63.24.64.0     | 16384                    | 63.24.127.255  |
| 128.1.1.254/20    | 255.255.240.0   | 128.1.0.0      | 4096                     | 128.1.15.255   |
| 208.100.54.209/30 | 255.255.255.252 | 208.100.54.208 | 4                        | 208.100.54.211 |

#Zadanie 4 Odpowiedz:
 
## Jaka jest maksymalna liczba adresów IP jakie można przydzielić hostom w sieci, która używa maski 255.255.255.224:
- [ ] 14
- [ ] 15
- [ ] 16
- [x] 30
- [ ] 31
- [ ] 62


## Jaki jest adres sieci w której znajduje się komputer o adresie 200.10.5.68/28:
- [ ] 200.10.5.56
- [ ] 200.10.5.32
- [x] 200.10.5.64
- [ ] 200.10.5.0

## Sieć 172.16.0.0/16 została podzielona na podsieci z maską /19. Ile powstało podsieci i po ile hostów się w nich mieści:
- [ ] 7 podsieci po 30 hostów
- [ ] 7 podsieci po 2046 hostów
- [ ] 7 podsieci po 8190 hostów
- [ ] 8 podsieci po 30 hostów
- [ ] 8 podsieci po 2046 hostów
- [x] 8 podsieci po 8190 hostów

## Które zdanie opisuje adres IP 10.16.3.65/23:
- [ ] Adres sieci to 10.16.3.0 z maska 255.255.254.0
- [x] Najniższy adres host w tej sieci to 10.16.2.1 z maską 255.255.254.0
- [ ] Ostatni poprawny adres hosta w tej sieci to 10.16.2.254 z maską 255.255.254.0
- [x] Adres rozgłoszeniowy (broadcast) w tej sieci to 10.16.3.255 z maską 255.255.254.0

## Adres interfejsu routera to 192.168.192.10/29. Jaki adres rozgłoszeniowy będzie używany przez komputery w tej sieci:
- [x] 192.168.192.15
- [ ] 192.168.192.31
- [ ] 192.168.192.63
- [ ] 192.168.192.127
- [ ] 192.168.192.255

## Ściąga
0 -> 0
1 -> 128
2 -> 192
3 -> 224
4 -> 240
5 -> 248
6 -> 252
7 -> 254
8 -> 255
