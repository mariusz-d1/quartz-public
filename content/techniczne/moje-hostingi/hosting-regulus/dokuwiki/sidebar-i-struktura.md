---
title: Sidebar i struktura
---

# Sidebar i struktura

## Założenie

Sidebar ma być prosty, czytelny i użyteczny. Nie powinien wyświetlać całego pełnego drzewa wszystkich stron na starcie.

## Cel

Lewy panel powinien działać jak spis działów, a nie jak pełny eksplorator wszystkich podstron.

## Główne działy

Planowane sekcje:
- strona główna
- kulinaria
- wypieki
- słodkości
- przetwory
- domowe środki
- ulubione / szybki dostęp

## Proponowana struktura treści

### Kulinaria
- jednogarnkowe
- pieczeń
- szynkowar

### Wypieki
- pieczywo
- ciasta
- chleby płaskie

### Przetwory
- octy
- przetwory sezonowe

### Domowe środki
- mydło kokosowe
- środki czystości
- receptury domowe

## Pomysł na stronę `sidebar`

```txt
====== Nawigacja ======

  * [[start|Strona główna]]

====== Kuchnia ======

  * [[kulinaria:start|Kulinaria]]
  * [[wypieki:start|Wypieki]]
  * [[slodkosci:start|Słodkości]]
  * [[przetwory_domowe:start|Przetwory]]

====== Dom ======

  * [[czyszczenie_domu:start|Domowe środki]]

====== Szybki dostęp ======

  * [[kulinaria:jednogarnkowe:start|Jednogarnkowe]]
  * [[wypieki:pieczenie:start|Pieczenie]]
```

## Uwagi do sprintdoc

W `sprintdoc` strona `sidebar` działa jako stałe menu boczne. Nagłówki w tej stronie mogą automatycznie tworzyć sekcje zwijane, co dobrze pasuje do podziału na kilka głównych działów. [web:21]

## Dalsze kroki

- [ ] uprościć obecną strukturę menu
- [ ] przygotować stronę `sidebar`
- [ ] rozważyć osobne sidebary dla wybranych namespace
- [ ] dopracować nazwy działów