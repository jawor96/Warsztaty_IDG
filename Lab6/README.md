# Usługa Multi-Protocol Gateway IDG

## Podstawowe usługi DataPower

Aby możliwe było korzystanie z funkcji DataPower, potrzebujemy skonfigurować usługi w ramach IDG. IBM DataPower Gateway pozwala na konfigurację wielu usług, które spełniają różne funkcjonalności w zależności od potrzeb.

Dzielimy je na różne typy. Wybrany typ zależy od:
- Potrzeby przetwarzania.
- Wykorzystywanych protokołów komunikacyjny.
- Typów serwerów aplikacji końcowych/wewnętrznych (back-end).

<img src="../images/Lab6_01.png" width="70%">

"Front side” definiuje interfejs klienta do usługi DataPower.Większość usług ma politykę przetwarzania, którą konfigurujesz tak, aby zapewniała funkcje DataPower potrzebne danej usłudze. „Back side” definiuje interfejs usługi wychodzącej DataPower do serwerów aplikacji końcowym (back-end).

Podstawowe usługi dostępne w ramach DataPower Gateway to:

<table>
  <thead>
    <tr>
      <th> XML Firewall — zabezpiecza i odciąża przetwarzanie XML z wewnętrznych aplikacji (back-end) opartych na XML. Obsługuje im. Filtrowanie ruchu, walidacja i weryfikacja danych, kontrola dostępu, wirtualizacja usługi, kryptografia na poziomie wiadomości i pola.</th>
      <th rowspan="3"> <img src="../images/Lab6_02.png" width="50%"> </th>
    </tr>
    <tr>
      <th> Multi-Protocol Gateway (MPGW) — odbiera komunikaty od klientów korzystających z różnych protokołów komunikacyjnych i wysyła komunikaty do usług back-end’owych za pośrednictwem różnych protokołów. Dodatkowo obsługuje funkcje podobne do XML Firewall. </th>
    </tr>
    <tr>
      <th> Web Service Proxy (WS-Proxy) — wirtualizuje i zabezpiecza aplikacje back-end’owe usług internetowych. Dodatkowo obsługuje funkcje podobne do XML Firewall.</th>
    </tr>
  </thead>
</table>



<img src="../images/Lab6_02.png" width="40%">
<img src="../images/Lab6_03.png" width="70%">
<img src="../images/Lab6_04.png" width="70%">
<img src="../images/Lab6_05.png" width="70%">
<img src="../images/Lab6_06.png" width="70%">
<img src="../images/Lab6_07.png" width="70%">
<img src="../images/Lab6_08.png" width="70%">
<img src="../images/Lab6_09.png" width="70%">
