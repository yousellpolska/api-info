# YOU SELL — Aplikacje API Allegro

## Informacje

Aplikacje wewnętrzne **YOU SELL Sp. z o.o.** — agencji e-commerce specjalizującej się w obsłudze sprzedawców na platformie Allegro.

## Format User-Agent

Wszystkie zapytania do API Allegro identyfikowane są nagłówkiem:

```
<NazwaAplikacji>/1.0.0 (+https://github.com/yousellpolska/api-info)
```

Zgodnie z art. 3.4.c Regulaminu REST API Allegro (wymóg obowiązkowy od 30.06.2026).

## Aplikacje obsługi konta klienta

Aplikacje rejestrowane na kontach poszczególnych klientów agencji. Każdy klient autoryzuje aplikację poprzez OAuth2 Device Code Flow, co umożliwia YOU SELL prowadzenie dla niego obsługi na platformie Allegro.

### Zakres uprawnień

| Scope | Opis |
|-------|------|
| `allegro:api:sale:offers:read` | Odczyt danych o ofertach |
| `allegro:api:sale:offers:write` | Tworzenie, edycja, łączenie i zamykanie ofert |
| `allegro:api:sale:settings:read` | Odczyt ustawień sprzedaży |
| `allegro:api:orders:read` | Odczyt informacji o zamówieniach |
| `allegro:api:billing:read` | Odczyt salda i opłat na koncie |
| `allegro:api:payments:read` | Odczyt historii płatności |
| `allegro:api:campaigns` | Zgłaszanie ofert do kampanii promocyjnych Allegro (Strefa Okazji, oznaczenia SUPERCENA / GNC) |

### Obszary zastosowania

- Monitorowanie cen minimalnych i zmian ofert
- Śledzenie zamówień i transakcji
- Analiza kosztów sprzedaży i rozliczeń
- Generowanie raportów analitycznych i forecastów
- Zarządzanie kartami ofert (opis, parametry, zdjęcia lifestyle PKU)
- Zgłaszanie ofert do kampanii promocyjnych Allegro (Strefa Okazji, oznaczenia SUPERCENA / GNC)

## Aplikacja agencyjna

Aplikacja zarejestrowana na koncie agencyjnym YOU SELL — do zarządzania kampaniami Allegro Ads klientów agencji poprzez Agency ADS API.

### Zakres uprawnień

| Scope | Opis |
|-------|------|
| `allegro:api:ads` | Zarządzanie kampaniami Allegro Ads |

## Operator

**YOU SELL Sp. z o.o.**
ul. Tczewska 87h/2, 83-112 Rokitki

- Email: biuro@yousell.pl
- Tel: 505 707 470
- WWW: https://yousell.pl

## Wersja

2.0.0 (22.04.2026) — zunifikowana konwencja nazw aplikacji `YOU SELL SYSTEM - <nazwa klienta>`
