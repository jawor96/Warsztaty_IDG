# Narzędzia administracyjne i Troubleshooting IDG

## Procedura wstępna - utworzenie przykładowej konfiguracji

W ramach tego ćwiczenia utworzysz przykładową domenę, w której skonfigurujesz przykładowe usługi, które pozwolą Ci zapoznać się w kolejnych ćwiczeniach z funkcjami monitorowania i rozwiązywania problemów dostępnych w bramie IDG.

1. Na stacji roboczej w przeglądarce wywołaj adresIP DPG wykorzystywany w poprzednich ćwiczeniach: `https://adresIP:9090`i poczekaj na pojawienie się ekranu logowania.

<img src="../images/Lab4_01.png" width="40%">

2. Zaloguj się, do domeny `default` korzystając z interfejsu WebGUI używając skonfigurowanego uprzednio hasła:

```
Username: admin
Password: P@ssw0rd!
```
3. W celu utworzenia nowej domeny w wyszukiwarce wpisz: `Application Domain` i wybierz tą opcję, następni kliknij przycisk `Add`.

<img src="../images/Lab4_04.png" width="70%">

4. W otwartej zakładce `Application Domain` w polu `Name:` wprowadź nazwę nowej domeny: `adminsitration-debug`. W dolnej części strony zaznacz opcję `Enable Auditing` and `Enable Logging`. Pozostałe opcje pozostaw z domyślnymi ustawieniami, zatwierdź zmiany wybierając przycisk `Apply`, na końcu zapisz wprowadzone zmiany na stałe wybierając `Save Configuration` w prawym górnym rogu.

<img src="../images/Lab5_01.png" width="70%">

5. Przejdź do utworzenia przykładowej usługi XML, która posłuży nam do testowania poszczególnych ustawień i mechanizmów monitorowania platformy. W tym celu przechodzimy do nowo utworzonej domeny `administration-debug` wybierając jej nazwę w prawym górnym rogu platformy.

<img src="../images/Lab5_02.png" width="70%">

6. W celu utworzenia nowej usługi looback XML w wyszukiwarce wpsiz: `Edit XML Firewall` i wybierz tą opcję, następnie wybierz `Add Advanced`.

<img src="../images/Lab5_03.png" width="70%">

7. W oknie `Configure XML Firewall` w polu **Name** wpisz: `LoopBackXMLService`, z listy **Type** wybierz `Loopback`,  w polu **Port Number** wpisz `3223`, z listy **Request Type** wybierz `XML`, z listy **Request attachment processing mode** wybierz `Allow`. Wybierz znak `+` umieszczony obok listy `Procesing Policy`, aby dodać politykę przetwarzania wiadomości.

<img src="../images/Lab5_04.png" width="70%">

8. W otwartym oknie `Configure XML Firewall Style Policy` w polu **Policy Name** wpisz `accept`, następnie kliknij przycisk `New Rule` co spowoduje dodanie nowej reguły o nazwie `accept_rule_0`, nie zmieniaj `Rule Destination` na koniec kliknij dwa razy akcję oznaczoną znakiem `=`umieszczoną w środkowej części okna.

<img src="../images/Lab5_05.png" width="70%">

9. W otwartym oknie `Configure Matching Action` wybierz przycisk `+` umieszczony obok listy **Matching Rule**.

<img src="../images/Lab5_06.png" width="70%">

10. W otwartym oknie `Configure Matching Rule` wpisz `match-all-url` i wybierz przycisk `Add`.

<img src="../images/Lab5_07.png" width="70%">

11. W otwartym oknie `Edit Rules` wybierz z listy **Matching type** `URL`, w polu **URL match** wpisz znak `*` i zakończ wybierając przycisk `Apply`.

<img src="../images/Lab5_08.png" width="70%">

12. Po powrocie do okna `Configure Matching Rule` wybierz `Apply`.

<img src="../images/Lab5_09.png" width="70%">

13. Po powrocie do okna `Configure a Matching Action` upewnij się, że na liście **Matching Rule** figuruje Twoja reguła `match-all-uri` i wybieramy `Done`.

<img src="../images/Lab5_10.png" width="70%">

14. Po powrocie do okna `Configure XML Firewall Style Policy` kliknij przycisk `Apply Policy` i zamykamy okno.

<img src="../images/Lab5_11.png" width="70%">

15. Po powrocie do okna `Configure XML Firewall` upewnij się, że na liście **Processing Policy** wybrana jest Twoja polityka `accept`, na koniec kliknij `Apply`.

<img src="../images/Lab5_12.png" width="70%">

16. Zapisz wprowadzone zmiany wybierając `Save Configuration` w prawym górnym rogu.

## Sprawdzanie właściwości i statusu bramy oraz zdefiniowanych w niej obiektów z poziomu WebGUI

1. Przed przystąpieniem do realizacji tego ćwiczenia wróć do domeny `default` wybierając jej nazwę w prawym górnym rogu ekranu.

<img src="../images/Lab5_13.png" width="70%">

2. Brama DPG posiada bardzo wiele widoków pozwalających na sprawdzanie statusów własnej pracy i informacji dotyczących urządzenia, w poniższych ćwiczeniach przetestujesz jedynie te najbardziej istotne. W celu zapoznania się ze wszystkimi dostępnymi opcjami i samodzielnego sprawdzenia wystarczy przejść do menu: `Status`

<img src="../images/Lab5_14.png" width="70%">

3. Część informacji zbierana jest w charakterze statystyk, które mogą być domyślnie wyłączone, w celu ich włączenia w polu wyszukiwania wpisz `Statistic Settings`, a następnie wybierz tą opcję.  Następnie zaznacz opcję `Enabled` w polu **Administrative state** i wciśnij przycisk `Apply`.

<img src="../images/Lab5_15.png" width="70%">

4. Zapisz wprowadzone zmiany wybierając `Save Configuration` w prawym górnym rogu.
5. W celu wyświetlenia informacji dotyczących wersji IDG i firmware w polu wyszukiwania wpisz `Firmware Information` i wybierz tą opcję.

<img src="../images/Lab5_16.png" width="70%">

6. W celu wywoływania informacji o dostępnych funkcjach i modułach w polu wyszukiwania wpisz `Device Features` i wybierz tą opcję. Zapoznaj się z wyświetlonymi informacjami.

<img src="../images/Lab5_17.png" width="70%">

7. W celu wywoływania informacji o dostępnych bibliotekach i ich wersjach w polu wyszukiwania wpisz `Librarary Information` i wybierz tą opcję. Zapoznaj się z wyświetlonymi informacjami

<img src="../images/Lab5_18.png" width="70%">

8. W celu wywoływania statystyk użycia w polu wyszukiwania wpisz `System Usage` i wybierz tą opcję. Zapoznaj się z wyświetlonymi statystykami.

<img src="../images/Lab5_19.png" width="70%">

9. W celu wyświetlenia statystyk wykorzystania procesora w polu wyszukiwania wpisz `CPU Usage` i wybierz tą opcję.  Zapoznaj się z wyświetlonymi statystykami.

<img src="../images/Lab5_20.png" width="70%">

10. W celu wyświetlenia statystyk wykorzystania pamięci w polu wyszukiwania wpisz `Memory Usage` i wybierz tą opcję.  Zapoznaj się z wyświetlonymi statystykami

<img src="../images/Lab5_21.png" width="70%">

11. W celu wyświetlenia statystyk wykorzystania pamięci per domena w polu wyszukiwania wpisz `Domain Memory Usage` i wybierz tą opcję. Zapoznaj się z wyświetlonymi statystykami

<img src="../images/Lab5_22.png" width="70%">

12. W celu wyświetlenia statystyk wykorzystania pamięci przez poszczególne usługi w polu wyszukiwania wpisz `Service Memory Usage` i wybierz tą opcję. W domenie `default`, możesz przełączać się pomiędzy bieżącą domeną a wszystkimi domenami, korzystając z przycisku umieszczonego nad statystykami. Zapoznaj się z wyświetlonymi statystykami.

<img src="../images/Lab5_23.png" width="70%">

13. W celu wyświetlenia statystyk dotyczących systemu plików w polu wyszukiwania wpisz `Filesystem Information` i wybierz tą opcję. Zapoznaj się z wyświetlonymi statystykami.

<img src="../images/Lab5_24.png" width="70%">

14. W celu wyświetlenia statystyk dotyczących transakcji w polu wyszukiwania wpisz `Transaction Rate` i wybierz tą opcję, następnie wybierz przycisk `Show All Domains`. Zapoznaj się z wyświetlonymi statystykami. Zwróć uwagę, że statystyki muszą być włączone w każdej domenie, aby móc wyświetlić informację.

<img src="../images/Lab5_25.png" width="70%">

15. W celu wyświetlenia statystyk dotyczących czasu trwania transakcji w polu wyszukiwania wpisz `Transaction Times` i wybierz tą opcję, następnie wybierz przycisk `Show All Domains`. Zapoznaj się z wyświetlonymi statystykami. Zwróć uwagę, że statystyki muszą być włączone w każdej domenie

<img src="../images/Lab5_26.png" width="70%">

16. W celu wyświetlenia informacji statusach portów TCP w polu wyszukiwania wpisz `TCP Port Status` i wybierz tą opcję. Zapoznaj się z wyświetlonymi informacjami

<img src="../images/Lab5_27.png" width="70%">

17. W celu wyświetlenia informacji o dostępnych usługach w polu wyszukiwania wpisz `Active Services` i wybierz tą opcję, następnie wybierz przycisk `Show All Domains`. Zapoznaj się z wyświetlonymi informacjami.

<img src="../images/Lab5_28.png" width="70%">

18. W celu wyświetlenia informacji o statusie poszczególnych obiektów w polu wyszukiwania wpisz `Object Status` i wybierz tą opcję, następnie wybierz przycisk `Show All Domains`. Postarajnsię odnaleźć na liście informacje dotyczące usługi zdefiniowanej na początku tego ćwiczenia. 

<img src="../images/Lab5_29.png" width="70%">

## Konfiguracja logowania (Log Targets i poziomy logowania)

W tym ćwiczeniu zapoznamy się dostępnymi poziomami logowania i możliwościami wysyłania logów do zewnętrznych usług logowania/indeksacji logów

1. W tym celu przejdź do nowo utworzonej domeny `administration-debug` wybierając jej nazwę w prawym górnym rogu platformy.

<img src="../images/Lab5_30.png" width="70%">

2. Aby wyświetlić logi systemu DPG dla domeny `administration-debug` w polu wyszukiwania wpisz `System Logs` lub wybierz ikonę `View Logs` w głównej konsoli. 

<img src="../images/Lab5_31.png" width="70%">

3. Po  przejściu do podglądu logów zwróć uwagę na poziomy logowania jakie są tam wyświetlone. Domyślnie brama DPG loguje informacje o poziomie **notice** lub większym. Zwróć uwagę, że możesz zawężać informacje według poziomu logowania czy obiektu (w domenie `default` także według domeny) . Korzystając z dostępnych filtrów postaraj się zawęzić informacje do obiektu **mgmt** i poziomu logowania **warning**. Zwróć uwagę, że wybranie poziomu logowania zawęża informacje do poziomu wygranego lub wyższego poziomu logowania – przy zaznaczeniu **warning** powinieneś widzieć też informacje oznaczone jako **error**.

<img src="../images/Lab5_32.png" width="70%">

4. W celu zwiększenia poziomu szczegółowości logów w polu wyszukiwania wpisz `Troubleshooting` i wybierz tą opcję. Następnie w sekcji `Logging` wybierz z listy **Log level** `debug`. Zakończ wybierając przycisk `Set Log Level`. Pamiętaj, logowania na poziomie `debug` nie powinno być wybierane w normalnych warunkach pracy systemu, wpływa ono negatywnie na wydajność pracy bramy.

<img src="../images/Lab5_33.png" width="70%">

5. Na koniec ćwiczeń nauczysz się wysyłać logi to "zewnętrznego” repozytorium, którym będzie zdefiniowana przez Ciebie uprzednio usługa. W tym celu w polu wyszukiwania wpisz `Log Target` i wybierz tą opcję, następnie wybierz przycisk `Add`.

<img src="../images/Lab5_34.png" width="70%">

6. W otwartym oknie `Log Target` w polu **Name** wpisz `XMLLogTarget`, z listy **Target Type** wybierz `SOAP`, z listy **Log Format** wybierz `XML`, w polu **URl** wpisz `http://adresIP:3223`, gdzie adresIP to uprzednio ustalony adres bramy, na koniec przejdź na zakładkę `Event Subscription`.

<img src="../images/Lab5_35.png" width="70%">

7. W zakładce `Event Subscription` wybierz przycisk `Add`.

<img src="../images/Lab5_36.png" width="70%">

8. W otwartym oknie `Edit Event subscription` wybierzmy z listy **Event Category**: `mgmt`, z listy **Minimum event priority** wybierzmy `error`, a na koniec wybierz `Apply`.

<img src="../images/Lab5_37.png" width="70%">

9. Na koniec upewnij się, że Twoja subskrypcja znajduje się na liście w tabeli i następnie wybierz `Apply`.

<img src="../images/Lab5_38.png" width="70%">

10. Zdefiniowałeś “zewnętrzne” repozytorium logów. Przetestujesz jego działanie w późniejszych ćwiczeniach.
11. Zapisz wprowadzone zmiany wybierając `Save Configuration` w prawym górnym rogu.

## Raportowanie błędów 

W tym ćwiczeniu nauczysz się mechanizmów zbierania raportów błędów w celu ich zgłoszenia do obsługi wsparcia IBM.

1. Aby przygotować raport błędów dla działu wsparcia firmy IBM w polu wyszukiwania wpisz `Troubleshooting` i wybierz tą opcję, następnie w sekcji **Raporting** wybierz `Generate Error Raport`. Zwróć uwagę, że istnieje możliwość wysłania raportu przy użyciu protokołu SMTP

<img src="../images/Lab5_39.png" width="70%">

2. W oknie **Execute Action** wybierz `Confirm`.

<img src="../images/Lab5_40.png" width="40%">

3. Po wyświetleniu akcji **Action completed successfully** wybierz `Close`.

<img src="../images/Lab5_41.png" width="70%">

4. Następnie skorzystaj z odnośnika `View Error Raport` umieszczone w sekcji **Reporting**.  Zapisz plik z raportem błędu na komputerze.

<img src="../images/Lab5_42.png" width="70%">

5. Wyświetl zawartość pobranego pliku z raportem błędu - zwróć uwagę na jego format.

## Narzędzia do przeprowadzania diagnostyki sieci (PING, Connection Test, Przechwytywanie pakietów, Probes)

W tym ćwiczeniu zapoznasz się z dostępnymi narzędziami pozwalającymi na diagnostykę i analizę połączeń sieciowych i działania usług.

1. W celu skorzystania z narzędzia **Ping** w polu wyszukiwania wpisz `Troubleshooting` i wybierz tą opcję, następnie w sekcji **Networking Ping** **Remote Remote Host** wpisz adresIP twojej bramy

<img src="../images/Lab5_43.png" width="70%">

2. W otwartym oknie **Execute Action** wybierz `Confitrm`. Na koniec wybierz `Close`.

<img src="../images/Lab5_44.png" width="50%">

3. Powtórz test zmieniając ostatni oktet adresu IP na losową liczbę inną niż wpisana dotychczas, aby zaobserwować błąd.
4. Następnie w sekcji **Networking TCP Connection Test Remote Host** wpisz adresIP Twojej bramy, w polu port wpisz `3223`, na koniec wybierz przycisk `TCP Connection Test`.

<img src="../images/Lab5_45.png" width="70%">

5. W otwartym oknie **Execute Action** wybierz `Confitrm`. Na koniec wybierz `Close`.

<img src="../images/Lab5_46.png" width="70%">

6. Powtórz test zmieniając numer portu np. na `3224`, aby zaobserwować nieudane połączenie.
7. Zdefiniujesz czujkę (ang. Probe) na skonfigurowanym uprzednio serwisie, aby móc obserwować transakcje jakie obsługiwane są przez daną usługę.  W tum celu przejdź na zakładkę **Probe** i odnajdź zdefiniowany uprzednio serwis `LoopBackXMLService` i wybierz umieszczony obok niego przycisk `Add Probe`.

<img src="../images/Lab5_47.png" width="70%">

8. W otwartym oknie **Action Completed successfully** wybierz przycisk `Close`.

<img src="../images/Lab5_48.png" width="70%">

Zwróć uwagę, że na górze interfejsu pojawi się dodatkowe ostrzeżenie: `Probe is enabled`, which impacts performance. Czujki powinny być deaktywowane po zakończeniu testowania.

9. Teraz przejdź do wygenerowania zrzutu pakietów przy użyciu narzędzi do przechwytywania pakietów. W tym celu musimy przejść do domeny default wybierając jej nazwę w prawym górnym rogu ekranu

<img src="../images/Lab5_49.png" width="50%">

10. W celu skorzystania z narzędzia **PCAP** w polu wyszukiwania wpisz `Troubleshooting` i wybierz tą opcję, następnie w sekcji **Packet Capture** wybierz w polu **Interface Type**: `Ethernet Interface`, w polu **Interface Name**: `eth0`, w polu **Mode** wybierz `Continious`, na koniec wybierz `Start Packet Capture`.

<img src="../images/Lab5_50.png" width="70%">

11. W otwartym oknie **Execute Action** wybierz `Confirm`.

<img src="../images/Lab5_51.png" width="60%">

12. Następnie wybierz `Close`.
13. Wygenerujemsz teraz **Testowe Zdarzenie Logowania**, które powinno być przesłane do naszego serwisu. W tym celu przejdź do domeny `administration-debug`, wybierając jej nazwę w prawym górnym rogu platformy. 
14. W polu wyszukiwania wpisz `Troubleshooting` i wybierz tą opcję, a następnie w sekcji **Logging Generate Log Event** z listy **Log Category** wybierz `mgmt`, z **Log Level** wybierz `Error`, w polu **Log Massage** wpisz `This is TEST!!!`  na koniec wybierz przycisk `Generate Log Event`.

<img src="../images/Lab5_52.png" width="70%">

15. W otwartym oknie **Execute Action** wybierz `Confirm`. Po wykonaniu testu wybierz `Close`.

<img src="../images/Lab5_53.png" width="70%">

16. Przejdź do zakładki **Probes**, następnie odnajdź swoją czujkę wyświetloną obok serwisu `LoobBackXMLService` i wybierz ikonę **Lupy** aby wyświetlić transakcje.

<img src="../images/Lab5_54.png" width="70%">

17. W otwartym oknie powinieneś widzieć połączenia z serwisem. Jeśli w Twoim przypadku lista jest pusta skorzystaj z przycisku **Refresh**. Jeśli nadal nic nie widzisz być może popełniłeś literówkę w konfiguracji serwisu lub źródła logowania. Sprawdź logi w razie wątpliwości poproś o pomoc prowadzącego.
18. Zwróć uwagę, że na liście widać adres URL wchodzący i wychodzący, regułę która przepuściła połączenie i adres klienta. Wybierz ikonę **lupy** umieszczoną obok połączenia, aby uzyskać dostęp do szczegółów danego połączenia.


<img src="../images/Lab5_55.png" width="70%">

19. W otwartym oknie danego połączenia zwróć uwagę, że masz dostęp do szeregu szczegółowych informacji takich jak np. **Nagłówki Żądania**.

<img src="../images/Lab5_56.png" width="70%">

20. Teraz zatrzymaj czujkę wybierając przycisk `Disable` umieszczony obok naszego serwisu **LooopBackXMLService**. 

<img src="../images/Lab5_57.png" width="70%">

21. W otwarym oknie **Action complited successfully!** wybieramy przycisk `Close.`.

<img src="../images/Lab5_58.png" width="70%">

22. Zatrzymasz też przechwytywanie pakietów w tym celu musimy przejść do domeny `default` wybierając jej nazwę w prawym górnym rogu ekranu.
23. W celu zatrzymania przechwytywania pakietów polu wyszukiwania wpisz `Troubleshooting` i wybierz tą opcję, następnie w sekcji  **Packet Capture Stop Packet Capture** wybierz w polu **Interface Type**: `Ethernet Interface`, w polu **Interface Name**: `eth0`,  na koniec wybierz `StopPacket Capture`.

<img src="../images/Lab5_59.png" width="70%">

24. Plik może zostać pobrany bezpośrednio z linku w sekcji przechowywania lub z sytemu plików DPG. Aby pobrać plik ze zrzutem pakietów z systemu plików w polu wyszukiwania wpisz `File Management` i wybierz tą opcje, następnie w eksploratorze plików wybierz katalog `Temporary` i wskaż plik `capture.pcap.001`. Zapisz plik na lokalnym komputerze.

<img src="../images/Lab5_60.png" width="70%">

25. Plik ten można poddać analizie np. w programie WireShark. Program WireShark powinien być dostępny na stacjach. Aby załadować plik wskaż go wykorzystają opcję `Plik -> Otwórz (File -> Open)`. W Filtrze możesz być zmuszony wybrać `All-Files`. Możesz też zmienić rozszerzenie pliku na `*.pcap`. Możesz poeksperymentować z wyszukiwaniem danych korzystając z różnych filtrów, program będzie je podpowiadał np: `tcp.port == 9090` lub `tcp.port == 3223`.

