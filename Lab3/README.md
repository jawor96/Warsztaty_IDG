# Zarządzanie IBM DataPower Gateway

> [!WARNING]
> Wszystkie ćwiczenia wykonujemy w kontekście użytkownika "admin", chyba że będzie napisane inaczej.

## Domeny aplikacyjne – zarządzanie uprawnieniami

1. Wybierz z menu `Application domain` z drzewa `Administration -> Configuration`.
2. Kliknij `Add`, aby dodać nową domenę.

<img src="../images/Lab3_01.png" width="70%">

3. Dodaj domenę o nazwie `dev`, z pola `Visible domains` usuń domenę domyślną, resztę ustawień pozostawić bez zmian. Zaaplikuj zmiany i zapisz konfigurację.

<img src="../images/Lab3_02.png" width="70%">

4. Wróć do głównego ekranu i wejdź w zarządzanie plikami (`File Management`).

<img src="../images/Lab3_03.png" width="70%">

5. Przełącz się na domenę `dev`.

<img src="../images/Lab3_04.png" width="70%">

6. Po przełączeniu się na nową domenę aplikacyjną automatycznie zostałes przekierowany do głównego ekranu. Wejdź ponownie z zarządzanie plikami i porównaj widoczność plików/katalogów. Pliki z domeny `default` nie są widoczne w kontekście domeny `dev`.

<img src="../images/Lab3_05.png" width="70%">

7. Wróć do zarządzania domenami aplikacyjnymi (wcześniej przełączając się na domyślną domenę `default`).

<img src="../images/Lab3_06.png" width="70%">

8. Wyświetl szczegóły domeny `dev` (klikając na nazwę domeny), a następnie dodaj widoczność domeny `default`. Zaaplikuj i zapisz zmiany.

<img src="../images/Lab3_07.png" width="70%">

9. Dodaj nową domenę o nazwie `tst`, a w widoczności domen dodaj obie domeny, zarówno `default` jak i `dev`. Pozostałe parametry pozostaw bez zmian. Zaaplikuj i zapisz zmiany.

<img src="../images/Lab3_08.png" width="70%">

10. Uruchom zarządzanie plikami w domenie `default`. Zwrócić uwagę na widoczność podkatalogów `dev` i `tst` w wielu katalogach.

<img src="../images/Lab3_09.png" width="70%">

11. Porównaj listę katalogów w domenie `dev`, gdy została dodana widoczność z domyślnej domeny. Pojawił się `store:`.

<img src="../images/Lab3_10.png" width="70%">

12. Natomiast w domenie `tst`, mamy dodatkowo widoczny  folder `dev:`.

<img src="../images/Lab3_11.png" width="70%">