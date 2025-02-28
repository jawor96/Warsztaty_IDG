# Zapoznanie się z interfejsem administracyjnym IDG

> [!WARNING]
> Na poniższych przykładach i zrzutach ekranów IP DataPower jest 192.168.226.129, we wszystkich ćwiczeniach należy wykorzystać adres IP swojego DPG.

## Zarządzanie z wykorzystaniem CLI

1. Otwórz terminal i zaloguj się do interfejsu CLI via SSH, wpisując:

```ssh 192.168.226.129```

<img src="../images/Lab2_01.png" width="60%">

2. Sprawdź status usługi SSH, wpisując:

```show ssh```

<img src="../images/Lab2_02.png" width="50%">

3. Sprawdź status usługi WebUI, wpisując:

```show web-mgmt```

<img src="../images/Lab2_03.png" width="50%">

4. Sprawdź interfejsy sieciowe, wpisując:

```show interface```

<img src="../images/Lab2_04.png" width="70%">

5. Sprawdź skonfigurowane adresy IP, wpisując:

```show ipaddress```

<img src="../images/Lab2_05.png" width="70%">

6. Sprawdź konfigurację DNS wpisując:

```
show dns
show name-servers
```

<img src="../images/Lab2_06.png" width="70%">

7. Zweryfikuj czy serwer DNS jest dostępny, wpisując:


```
ping 192.168.226.2
```

<img src="../images/Lab2_07.png" width="70%">

8. Wyświetl zawartość lokalnego katalogu i katalogu z konfiguracjami, wpisując:

```
config
dir local:
dir config:
exit
```

<img src="../images/Lab2_08.png" width="70%">

## Wykorzystanie REST API do zarządzania IDG

1. Z poziomu CLI uruchom zarządzanie via REST, po ok 1-2 min interfejs będzie dostępny pod wskazanym adresem i portem. Wykonaj serię komend:

```
config
rest-mgmt
show
admin-state enabled
exit
write memory
y
exit
```

<img src="../images/Lab2_09.png" width="70%">

2. Uruchom przeglądarkę i wywołaj adres REST (adres IP i port), przykładowy adres: `https://192.168.226.129:5554`

<img src="../images/Lab2_10.png" width="70%">

3. Wyświetl listę dostępnych endpoint'ów dla parametrów konfiguracji w interfejsie REST.

```https://192.168.226.129:5554/mgmt/config/```

<img src="../images/Lab2_11.png" width="70%">

4. Wyświetl konfigurację usługi rest-mgmt

```https://192.168.226.129:5554/mgmt/config/default/RestMgmtInterface/RestMgmt-Settings```

5. Przy pierwszym uruchomieniu zastrzeżonego URL należy najpierw zalogować się (użytkownik: `admin`, hasło: `P@ssw0rd!`).

<img src="../images/Lab2_12.png" width="70%">

6. Następnie wyświetli się sformatowana odpowiedź JSON konfiguracji usługi rest-mgmt:

<img src="../images/Lab2_13.png" width="70%">

### Zmiana TimeZone dla domyślnej domeny korzystając z REST.

1. Otwórz aplikację SopeUI (skrót na Pulpicie).
2. Stwórz nowy projekt REST i wpisz URI: `https://192.168.226.129:5554`.
3. Dla każdego zapytania należy ustawić metodę uwierzytelnienia (**Auth**) na **Basic** i podać użytkownika `admin` i hasło `P@ssw0rd!`.
4. Sprawdź aktualny status daty i czasu (ustawienia domyślne):

```GET /mgmt/status/default/DateTimeStatus```

<img src="../images/Lab2_14.png" width="80%">

5. Sprawdź aktualne ustawienia strefy czasowej:

```GET /mgmt/config/default/TimeSettings/Time```

<img src="../images/Lab2_15.png" width="80%">

6. Ustaw strefę czasową na naszą:

```PUT /mgmt/config/default/TimeSettings/Time/LocalTimeZone```

Payload (application/json):

```{"LocalTimeZone": "CET-1CEST"}```

<img src="../images/Lab2_16.png" width="80%">

7. Ponownie sprawdź aktualny status daty i czasu, ustawiony będzie nowy TimeZone:

```GET /mgmt/status/default/DateTimeStatus```

<img src="../images/Lab2_17.png" width="80%">

8. Zapisz nową konfigurację domeny:

```POST /mgmt/actionqueue/default```

Payload: `{"SaveConfig" : "0"}`

<img src="../images/Lab2_18.png" width="80%">

## DataPower WebUI

1. Zaloguj się do interfejsu Web DataPower: `https://192.168.226.129:9090`, korzystając z loginu i hasła:

```
Username: admin
Password: P@ssw0rd!
```

<img src="../images/Lab2_19.png" width="70%">

2. Zweryfikuj ustawienia strefy czasowej, w oknie wyszukiwania wpisać `Time Sett` i wybrać menu. Jeżeli ustawienia są inne niż `CET (Central Europe Time)` to zmienić na nie.

<img src="../images/Lab2_20.png" width="80%">

3. Wejdź na ustawienia usługi `Network -> Interface -> NTP service` i upewnić się, że jest wyłączona.

<img src="../images/Lab2_21.png" width="80%">

4. W tym samym drzewie nawigacji wejść w DNS settings i wyłączyć usługę, przestawić `Administrative state` na `disabled` i zaaplikuj zmiany.

<img src="../images/Lab2_22.png" width="80%">

5. Wrócić do głównego ekranu klikając `Control Panel`, a następnie przejść do `System Control`.

<img src="../images/Lab2_23.png" width="70%">

6. "Zepsuj" czas, cofając go np. o 4 godziny.

<img src="../images/Lab2_24.png" width="80%">

7. Wróć do ustawień `NTP Service`, dodaj nowy serwer `time.google.com` oraz włączyć `Administrative state (enabled)`. Potwierdź zmiany (`Apply`). Przy okazji zweryfikować na górnej belce, czy mamy "zepsuty" czas. Po akceptacji zmian, status usługi będzie nieaktywny, bo nie może rozwiązać nazwy serwera (wcześniej wyłączyliśmy konfigurację DNS).

<img src="../images/Lab2_25.png" width="80%">

8. Wróć do ustawień DNS i włączyć usługę (zaaplikuj zmiany). Czas na belce będzie jeszcze błędny.

<img src="../images/Lab2_26.png" width="80%">

9. Wróć do ustawień `NTP service`, czas powinien być prawidłowy oraz usługa NTP powinna być uruchomiona.

<img src="../images/Lab2_27.png" width="80%">

10. Pamiętaj, aby zapisać zmiany dokonane w konfiguracji IDG, klikając `Save Configuration`.

<img src="../images/Lab2_28.png" width="40%">
