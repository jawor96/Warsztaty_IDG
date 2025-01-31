# Usługa Multi-Protocol Gateway IDG

Celem tego ćwiczenia jest poznanie usługi Multi-Protocol Gateway (MPGW) oraz podstawowa konfiguracja następujących funkcji:
- Dynamic-backend (routing).
- Zabezpieczenia na poziomie FSH.
- Transform with XSLT style sheet.
- XML Schema Validation.
- AAA Policy.
- DataPower Gateway Script.

Podczas tego ćwiczenia skonfigurujemy usługę MPGW o nazwie MPGW_BankService, której celem będzie przekierowanie zapytania do odpowiedniego serwisu back-end’owego, który zwróci odpowiedź w zależności od zapytania. Podczas tworzenia usługi MPGW będziemy sukcesywnie dodawać kolejne reguły i zabezpieczenia usługi.

## Dostęp do plików i katalogów na laptopie

Wszystkie pliki wymagane do wykonania tego ćwiczenia znajdują się w następującym folderze lokalnym:

`C:\DataPowerAdminTraining\Lab7`

## Podstawowa konfiguracja MPGW
