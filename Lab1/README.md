# Instalacja i inicjalizacja bramki DPG

## Wersje DataPower do pobrania z repozytorium IBM

Istnieją trzy podstawowe wersje obrazów VMWare bramy DataPower, które można pobrać i zainstalować w środowisku wirtualizacyjnym:

1. DataPower Gateway for Production
2. DataPower Gateway for Non-Production
3. DataPower Gateway for Developers

Powyższe wersje różnią się od siebie **sposobem licencjonowania**, a także **modułami dodatkowymi**, które w wersji „for Developers” są dostępne i aktywowane, a w wersji Non-Production & Production mogą wymagać włączenia i aktywowania. Pełna lista modułów w zależności od wersji znajduje się pod tym [linkiem w dokumentacji IBM](https://www.ibm.com/docs/en/datapower-gateway/10.5.x?topic=management-available-modules-by-product).

## Dostęp do plików i katalogów na laptopie

Wszystkie pliki wymagane do wykonania tego ćwiczenia znajdują się w następującym folderze lokalnym:

    C:\DataPowerAdminTraining\Lab1

W powyższym folderze znajduje się obraz bramy DataPower (plik: `idg10502.ova`) oraz narzędzie `ovftool`, które służy do rozpakowywania plików `ova` oraz `ovf` wprost do postaci maszyn wirtualnych. 

## Rozpakowanie obrazu maszyny wirtualnej DataPower

1. Aby rozpocząć należy otworzyć terminal i wykonać serię komend jak poniżej:

<img src="../images/Lab1_01.png" width="70%">

```
cd C:\DataPowerAdminTraining\Lab1

ovftool\ovftool.exe idg10502.ova datapower-vm
```

Narzędzie `ofvtool` rozpocznie proces rozpakowywania pliku `ova`, a wynik zapisze w katalogu `datapower-vm`.

2. W pierwszym kroku procesu należy zaakceptować licencje, wspisując `yes`.

<img src="../images/Lab1_02.png" width="50%">

Po akceptacji licencji rozpocznie się proces rozpakowywania dysków który potrwa kilka (lub kilkanaście) sekund. Ostatecznie powinniśmy uzystkać następujący rezultat:

<img src="../images/Lab1_03.png" width="50%">

Powinien zostać utworzony nowy katalog `datapower-vm`, a w nim pliki maszyny wirtualnej.

<img src="../images/Lab1_04.png" width="50%">

## Import plików maszyny wirtualnej do VMWare Workstation

1. Uruchamiamy aplikację `VMWare Workstation Pro` korzystając ze skrótku na pulpicie.

<img src="../images/Lab1_05.png" width="30%">

2. Wybierz opcję `Open a Virtual Machine` i wskaż na katalog: `C:\DataPowerAdminTraining\Lab1\datapower-vm\idg10502.lts.nonprod`, a następnie `idg10502.lts.nonprod.vmx`.

<img src="../images/Lab1_07.png" width="50%">

<img src="../images/Lab1_08.png" width="50%">

3. Po chwili maszyna powinna pojawić się w aplikacji VMWare Workstation. Zanim zostanie włączona należy jeszcze wykonać dwa kroki:

- Migrację obrazu do wersji VMware 12.
- Zmianę parametrów maszyny wirtualnej – m.in ilości rdzeni przydzielonych do maszyny.

<img src="../images/Lab1_09.png" width="30%">

4. Z menu należy wybrać następującą opcję: `VM -> Manage -> Change Hardware Compability`

<img src="../images/Lab1_10.png" width="40%">

5. Należy wcisnąć przycisk `Next` i przejść do następnego ekranu:

<img src="../images/Lab1_11.png" width="40%">

6. Na kolejnym ekranie należy zmienić domyślną opcję i zaznaczyć: `Alter this virtual machine`

<img src="../images/Lab1_12.png" width="40%">

7. Po kolejnym wciśnięciu przycisku `Next` należy potwierdzić chęć migracji przyciskiem `Finish`.

<img src="../images/Lab1_13.png" width="30%">

8. Po imporcie maszyny do środowiska VMWare, należy zmienić podstawowe parametr maszyny wirtualnej czyli np. ilość procesorów i rdzeni, a także rodzaj karty sieciowej. Laptop na którym wykonujemy ćwiczenia pozwala na uruchomienie maszyn wirtualnych z maksymalnie 4 rdzeniami.

<img src="../images/Lab1_14.png" width="30%">

9. Na ekranie edycji parametrów maszyny wirtualnej zaznaczamy ilość procesorów i rdzeni:

    Number of processors: 1
    Number of cores per processor: 4

10. Dodatkowo, należy zmienić tryb połączenia pierwszej karty sieciowej: `Network Adapter` z domyślnej wartości `Bridged (Automatic)` na `NAT`

<img src="../images/Lab1_16.png" width="50%">

11. Należy zatwierdzić zmianę wciskając przycisk `OK`.

Ostatecznie, konfiguracja powinna wyglądać następująco:

<img src="../images/Lab1_17.png" width="30%">

## Pierwsze uruchomienie maszyny DataPower Gateway

1. W tej chwili maszyna wirtualna jest gotowa do uruchomienia. Należy wcisnąć link oznaczony jako `Power on this virtual machine`
2. Rozpocznie się proces uruchamiania maszyny, a w nim konfiguracja najważniejszych parametrów DataPower Gateway.

<img src="../images/Lab1_18.png" width="50%">

3. Proces uruchamiania maszyny DataPower powinien się zatrzymać prosząc użytkownika o wprowadzenie domyślnych danych do logowania. Należy wpisać:

    login: admin
    password: admin

4. Po pomyślnym zalogowaniu, uruchamia się konfigurator, który przeprowadzi nam przez najważniejsze parametry systemu DataPower, które należy ustawić na samym początku.

<img src="../images/Lab1_19.png" width="50%">

5. W kolejnych krokach będziesz pytany o:

```
1.	Enable Secure Backup mode?: Y
2.	Confirm Secure Backup mode?: Y
3.	Enable Common Criteria Compability mode?: N
4.	Please enter new password: P@ssw0rd!
5.	Please re-enter new password to confirm: P@ssw0rd!
6.	Do you want to run the Installation Wizard? Y
7.	Step 1
8.	Do you want to configure network interfaces? Y
9.	Do you have this information? Y
10.	Do you want to configure the eth0 interfaces? Y
11.	Do you want to enable DHCP? Y
12.	Do you want to configure eth1 interface? N
13.	Do you want to configure eth2 interface? N
14.	Do you want to configure eth3 interface? N
15.	Step 2
16.	Do you want to configure network services? Y
17.	Do you want to configure DNS? N
18.	Do you want to define a unique system identified for the appliance? Y
19.	Enter a unique system identifier: idg1
20.	Do you want to configure remote management interface? Y
21.	Do you have this information? Y
22.	Do you want to enable SSH? Y
23.	Enter the local IP address [0 for all]: 0
24.	Enter the port number [22]: 22
25.	Do you want to enable WebGUI access? Y
26.	Enter the local IP address [0 for all]: 0
27.	Enter the port number [9090]: 9090
28.	Step 5
29.	Do you want to configure a user account that can reset passwords? N
30.	Step 6
31.	Do you want to configure the RAID array? N
32.	Step 7
33.	Do you want to review the current configuration? Y
34.	Do you want to save current configuration? Y
35.	Overwrite previously saved configuration? Y
```

<img src="../images/Lab1_20.png" width="50%">

6. Po zapisaniu konfiguracji, użytkownik jest proszony o akceptację umowy licencyjnej za pomocą interfejsu graficznego.

<img src="../images/Lab1_21.png" width="50%">

7. Aby dostać się przez przeglądarkę do interfejsu graficznego musimy poznać adres IP jaki został przydzielony maszynie DataPower poprzez DHCP. Pozostając w terminalu należy wykonać następujące komendy:

    configure
    show interface

<img src="../images/Lab1_22.png" width="50%">

8. Na stacji roboczej z której Panstwo korzystacie, adres IP może mieć inną wartość. Należy ją zapisać i wprowadzić do przeglądarki internetowej w postaci:

    https://adresIP:9090

Korzystając z przykładu powyżej, URL do interfejsu graficznego będzie następujący:

    https://192.168.226.129:9090

<img src="../images/Lab1_23.png" width="40%">

9. Przeglądarka ostrzeże przed niezaufanym certyfikatem. Należy zignorować tę informację i mimo to otworzyć stronę.

<img src="../images/Lab1_24.png" width="40%">

10. Zaloguj się, używając zmienionego wcześniej hasła:

    Username: admin
    Password: P@ssw0rd!

11. Następnie przejrzyj umowę licęcyjną i ją zaakceptuj.

<img src="../images/Lab1_25.png" width="40%">

12. Nie zamykaj żadnego z okien, poczekaj dłuższą chwilę (ok. 1 minuty). W tym czasie, maszyna DataPower aktywuje swoje wewnętrzne mechanizmy, aby za chwilę być gotowa to pracy.

<img src="../images/Lab1_26.png" width="40%">

13. W kolejnym kroku pojawia się ponownie ekran logowania. Należy wpisać te same dane:

    Username: admin
    Password: P@ssw0rd!

14. Pierwsze logowanie po akceptacji licencji również trwa trochę dłużej (ok. 20-40 sekund), a nastęnie użytkownik zostaje przeniesiony do ekranu głównego interfejsu DataPower. 

<img src="../images/Lab1_27.png" width="40%">

## Podstawowe kroki administracyjne po pierwszym zalogowaniu

Na tym etapie warto wykonać tych kilka podstawowych czynności administracyjnych:

1.	Wydłużenie czasu nieaktywności w interfejsie graficznym (na środowiskach deweloperskich i ewentualnie nie-produkcyjnych)
2.	Ustalenie własnych certyfikatów w interfejsie graficznym GUI

### Wydłużenie czasu nieaktywności w interfejsie graficznym

Aby zwiększyć ergonomię pracy w trakcie tego szkolenia dobrym pomysłem jest wydłużenie czasu nieaktywności interfejsu graficznego. Standardowo, użytkownik zostanie wylogowany po 600 sekundach co jest wartością właściwą wszędzie tam gdzie zależy nam na bezpieczenstwie. 

1. Na środowiskach deweloperskich lub szkoleniowych lepiej jest jednak wydłużyć ten czas na przykład do wartości 6000 sekund czyli 100 min. W tym celu w wyszukiwarce wpisz:

    web management

<img src="../images/Lab1_28.png" width="50%">

2. Zmień wartość parametru: `Idle timeou`t z 600 na 6000 [seconds]

3. Dodatkowo w zakładce `“Advanced”` mamy możliwość wgrania własnych certyfikatów (Custom TLS server profile), którymi DataPower będzie się przedstawiał użytkownikom w przeglądarce. 

Po wykonaniu zmian, należy wcisnąć przycisk `Apply`, a następnie w prawym górnym rogu `Save Configuration`.

<img src="../images/Lab1_29.png" width="40%">

> [!WARNING]
> Wszystkie zmiany jakie wprowadzamy przyciskami `Apply` są zapisywane w pamięci RAM urządzenia i aplikowane natychmiast. Wciśnięcie linku `Save Configuration` powoduje permanentne zapisanie tych zmian na dyskach DataPower-a. 

### Ustalenie własnych certyfikatów w interfejsie graficznym GUI

W tym samym miejscu (Web Management Service), na zakładce Advance mamy możliwość podmiany domyśnych certyfikatów prezentowanych przeglądarce przez serwer DataPower w konsoli graficznej. Nie będziemy ich teraz tutaj zmieniać, ale warto pamiętać, że jest to jedna z pierwszych rzeczy jakie wykonuje się po inicjalizacji nowej maszyny z urządzeniem DataPower.

<img src="../images/Lab1_30.png" width="50%">

## Podsumowanie

Ten skrypy przeprowadza Administratora przez pierwsze kroki związane z uruchomieniem urządzenia DataPower w środowisku VMWare.

