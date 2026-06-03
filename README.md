# YOU SELL — Aplikacje API Allegro

## Informacje

Aplikacje wewnętrzne YOU SELL Sp. z o.o. — agencji e-commerce
obsługującej sprzedawców na platformie Allegro.

To repozytorium jest wspólnym punktem informacyjnym dla wszystkich
aplikacji REST API zarejestrowanych przez YOU SELL. Każda aplikacja
identyfikuje się nagłówkiem User-Agent z linkiem do tego repozytorium,
zgodnie z art. 3.4.c Regulaminu REST API Allegro (wymóg od 30.06.2026).

## Format User-Agent

    <NazwaAplikacji>/1.0.0 (+https://github.com/yousellpolska/api-info)

## Model aplikacji

Dla każdego obsługiwanego konta sprzedawcy funkcje są rozdzielone na
osobne aplikacje zgodnie z zasadą najmniejszych uprawnień — każda
aplikacja ma wyłącznie scope'y niezbędne do swojej roli. Każdy
sprzedawca autoryzuje aplikacje samodzielnie przez OAuth2.

### 1. YOU SELL RAPORTY - <nazwa konta>

OAuth grant: authorization_code
Przeznaczenie: odczyt danych sprzedażowych i generowanie raportów
analitycznych. Aplikacja wyłącznie odczytuje dane — niczego nie
modyfikuje na koncie sprzedawcy.

| Scope                            | Opis                              |
|----------------------------------|-----------------------------------|
| allegro:api:sale:offers:read     | Odczyt danych o ofertach          |
| allegro:api:sale:settings:read   | Odczyt ustawień sprzedaży         |
| allegro:api:orders:read          | Odczyt informacji o zamówieniach  |
| allegro:api:billing:read         | Odczyt salda i opłat na koncie    |
| allegro:api:payments:read        | Odczyt historii płatności         |

### 2. YOU SELL SYSTEM - <nazwa konta>

OAuth grant: device_code
Przeznaczenie: odczyt danych do budowy bazy analitycznej oraz
zgłaszanie ofert do kampanii i programów promocyjnych Allegro.
Aplikacja nie posiada uprawnień do edycji ofert.

| Scope                            | Opis                              |
|----------------------------------|-----------------------------------|
| allegro:api:sale:offers:read     | Odczyt danych o ofertach          |
| allegro:api:sale:settings:read   | Odczyt ustawień sprzedaży         |
| allegro:api:orders:read          | Odczyt informacji o zamówieniach  |
| allegro:api:billing:read         | Odczyt salda i opłat na koncie    |
| allegro:api:payments:read        | Odczyt historii płatności         |
| allegro:api:campaigns            | Zgłaszanie ofert do kampanii      |
|                                  | i programów promocyjnych Allegro  |

### 3. YOU SELL DP - <nazwa konta>

OAuth grant: device_code
Przeznaczenie: zarządzanie cenami ofert (dynamic pricing).
Uprawnienie allegro:api:sale:offers:write wykorzystywane jest
wyłącznie do modyfikacji ceny — aplikacja nie zmienia opisu,
parametrów ani zdjęć ofert.

| Scope                            | Opis                              |
|----------------------------------|-----------------------------------|
| allegro:api:sale:offers:read     | Odczyt danych o ofertach          |
| allegro:api:sale:offers:write    | Modyfikacja ceny ofert            |
| allegro:api:orders:read          | Odczyt informacji o zamówieniach  |

## Obszary zastosowania

- Monitorowanie cen i zmian ofert
- Śledzenie zamówień i transakcji
- Analiza kosztów sprzedaży i rozliczeń
- Generowanie raportów analitycznych i prognoz
- Zarządzanie cenami ofert (dynamic pricing)
- Zgłaszanie ofert do kampanii i programów promocyjnych Allegro

## Operator

YOU SELL Sp. z o.o.
ul. Tczewska 87h/2, 83-112 Rokitki

- Email: biuro@yousell.pl
- Tel: 505 707 470
- WWW: https://yousell.pl

## Wersja

3.1.0 (03.06.2026) — rozdzielenie kompetencji: zgłaszanie ofert do
kampanii i programów promocyjnych Allegro przeniesione wyłącznie
do aplikacji YOU SELL SYSTEM; aplikacja YOU SELL DP ograniczona
wyłącznie do dynamic pricing (usunięcie scope allegro:api:campaigns).

3.0.0 (22.05.2026) — rozdzielenie aplikacji na 3 role
(RAPORTY / SYSTEM / DP) wg zasady najmniejszych uprawnień;
usunięto sekcję aplikacji agencyjnej ADS (osobny model połączenia).
