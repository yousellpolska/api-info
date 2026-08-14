# YOU SELL — Aplikacje API Allegro

## Informacje

Aplikacje operacyjne **agencji marketingowej** YOU SELL Sp. z o.o.,
wykorzystywane do obsługi kont sprzedawców na platformie Allegro
w ramach świadczonych im usług marketingowych, analitycznych
i operacyjnych.

Każda aplikacja jest autoryzowana **indywidualnie przez sprzedawcę**
w protokole OAuth2 — sprzedawca w panelu Allegro Developer wybiera
zakres uprawnień, jakie chce udzielić, i w każdej chwili może je
cofnąć. YOU SELL nie ma dostępu do konta sprzedawcy poza zakresem
jawnie autoryzowanym.

Kategoria aplikacji w panelu Allegro Developer: **Agencja marketingowa**.
Cel: świadczenie usług innym sprzedawcom.

To repozytorium jest wspólnym punktem informacyjnym dla wszystkich
aplikacji REST API zarejestrowanych przez YOU SELL. Każda aplikacja
identyfikuje się nagłówkiem User-Agent z linkiem do tego repozytorium,
zgodnie z art. 3.4.c Regulaminu REST API Allegro (wymóg od 30.06.2026).

## Format User-Agent

    <NazwaAplikacji>/1.0.0 (+https://github.com/yousellpolska/api-info)

Nazwa aplikacji w nagłówku User-Agent jest zawsze **1:1 zgodna** z nazwą
aplikacji zarejestrowanej w Allegro Developer, której token jest używany
w danym żądaniu (np. token sprzedawcy X → User-Agent ze ścisłą nazwą
aplikacji autoryzowanej przez sprzedawcę X).

## Model aplikacji

Dla każdego obsługiwanego konta sprzedawcy funkcjonuje **jedna aplikacja
per sprzedawca** — YOU SELL DP — obejmująca wszystkie funkcje operacyjne
(analityka, kampanie, dynamic pricing). Każdy sprzedawca autoryzuje
aplikację samodzielnie przez OAuth2 i kontroluje jej zakres niezależnie
od innych sprzedawców. Konsolidacja z modelu dwu-aplikacyjnego
(SYSTEM + DP) do jednej apki nastąpiła 14.08.2026 zgodnie z wymogiem
regulaminu REST API Allegro obowiązującym od 01.09.2026 (limit 1
aktywna aplikacja per konto sprzedawcy).

### YOU SELL DP - &lt;nazwa konta&gt;

OAuth grant: device_code
Przeznaczenie: skonsolidowana aplikacja operacyjna dla obsługi konta
sprzedawcy — budowa bazy analitycznej, zgłaszanie ofert do kampanii
i programów promocyjnych, zarządzanie cenami ofert (dynamic pricing).
Uprawnienie `allegro:api:sale:offers:write` wykorzystywane jest
wyłącznie do modyfikacji ceny — aplikacja nie zmienia opisu,
parametrów ani zdjęć ofert. Uprawnienie `allegro:api:sale:settings:write`
wykorzystywane jest wyłącznie do zarządzania ustawieniami sprzedaży
w zakresie umożliwiającym prawidłowe działanie automatyzacji cenowej
(np. minimalna cena, waluta).

| Scope                              | Opis                                        |
|------------------------------------|---------------------------------------------|
| allegro:api:sale:offers:read       | Odczyt danych o ofertach                    |
| allegro:api:sale:offers:write      | Modyfikacja ceny ofert                      |
| allegro:api:sale:settings:read     | Odczyt ustawień sprzedaży                   |
| allegro:api:sale:settings:write    | Modyfikacja ustawień sprzedaży (min. cena)  |
| allegro:api:orders:read            | Odczyt informacji o zamówieniach            |
| allegro:api:billing:read           | Odczyt salda i opłat na koncie              |
| allegro:api:payments:read          | Odczyt historii płatności                   |
| allegro:api:campaigns              | Zgłaszanie ofert do kampanii                |
|                                    | i programów promocyjnych Allegro            |

### YOU SELL SYSTEM - &lt;nazwa konta&gt; — DEPRECATED

Aplikacja **wycofana z użytku 14.08.2026** w ramach konsolidacji do
jednej apki per sprzedawca (YOU SELL DP). Wszystkie funkcje odczytu
danych sprzedażowych, kampanii i programów promocyjnych realizowane są
obecnie przez YOU SELL DP. Aplikacje YOU SELL SYSTEM zostaną usunięte
z panelu Allegro Developer do 28.08.2026 (przed wejściem w życie
nowego regulaminu 01.09.2026).

## Obszary zastosowania

- Monitorowanie cen i zmian ofert sprzedawcy
- Śledzenie zamówień i transakcji
- Analiza kosztów sprzedaży i rozliczeń
- Generowanie raportów analitycznych i prognoz
- Zarządzanie cenami ofert (dynamic pricing) — wyłącznie cena
- Zgłaszanie ofert do kampanii i programów promocyjnych Allegro
- Planowane: zarządzanie rabatami wielosztukowymi i promocjami
  sprzedażowymi (`/sale/loyalty/promotions`) w imieniu sprzedawcy

## Operator

**YOU SELL Sp. z o.o.** — agencja marketingowa
ul. Tczewska 87h/2, 83-112 Rokitki

- Email ogólny: biuro@yousell.pl
- Email kontakt operacyjny / API: tomasz@yousell.pl
- Tel: 505 707 470
- WWW: https://yousell.pl

Sprawy dotyczące zakresu aplikacji, scope'ów OAuth lub zgłoszenia
naruszeń regulaminu API prosimy kierować na **tomasz@yousell.pl**
(skrzynka prowadzona przez prezesa zarządu, kontakt operacyjny
techniczny i compliance).

## Wersja

3.4.0 (14.08.2026) — konsolidacja do jednej aplikacji per sprzedawca
(YOU SELL DP). Funkcje aplikacji YOU SELL SYSTEM (odczyt danych
analitycznych, zgłaszanie ofert do kampanii, odczyt zamówień i
rozliczeń) przeniesione do YOU SELL DP z rozszerzonym zakresem
scope. Aplikacje YOU SELL SYSTEM oznaczone jako DEPRECATED —
usunięcie zaplanowane na 28.08.2026. Konsolidacja zgodna z wymogiem
regulaminu REST API Allegro obowiązującym od 01.09.2026 (limit
1 aktywna aplikacja per konto sprzedawcy). YOU SELL DP obsługuje
teraz 8 scope OAuth2 zamiast dotychczasowych 3 — pełen zakres
uprawnień określony w sekcji "YOU SELL DP" powyżej.

3.3.0 (24.06.2026) — wycofanie aplikacji YOU SELL RAPORTY z modelu
operacyjnego. Funkcje odczytu danych sprzedażowych i generowania
raportów analitycznych realizowane są obecnie przez aplikację
YOU SELL SYSTEM, która posiada wymagane scope'y odczytu w ramach
jednej rejestracji per sprzedawca (ograniczenie liczby autoryzacji
po stronie sprzedawcy).

3.2.0 (08.06.2026) — doprecyzowanie modelu agencyjnego: jawne
określenie roli **agencji marketingowej** świadczącej usługi
innym sprzedawcom (kategoria 1:1 z panelem Allegro Developer);
podkreślenie indywidualnej autoryzacji OAuth2 przez każdego
sprzedawcę; jawna reguła zgodności User-Agent z nazwą zarejestrowanej
aplikacji; dodany dedykowany punkt kontaktowy compliance/API
(tomasz@yousell.pl).

3.1.0 (03.06.2026) — rozdzielenie kompetencji: zgłaszanie ofert do
kampanii i programów promocyjnych Allegro przeniesione wyłącznie
do aplikacji YOU SELL SYSTEM; aplikacja YOU SELL DP ograniczona
wyłącznie do dynamic pricing (usunięcie scope allegro:api:campaigns).

3.0.0 (22.05.2026) — rozdzielenie aplikacji na 3 role
(RAPORTY / SYSTEM / DP) wg zasady najmniejszych uprawnień;
usunięto sekcję aplikacji agencyjnej ADS (osobny model połączenia).
