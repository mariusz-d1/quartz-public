---
title: Mermaid - gantt w Quartz
description: Przykład diagramu Gantta w Mermaid z pokazaniem kodu i wyniku.
tags:
  - techniczne
  - mermaid
  - quartz
  - gantt
---

# Mermaid - gantt w Quartz

Diagram Gantta w Mermaid przydaje się do prostego pokazywania etapów prac, kolejności działań i zależności czasowych.

## Prosty gantt

### Kod

````md
```mermaid
gantt
    title Aktualizacja i publikacja notatek
    dateFormat YYYY-MM-DD
    section Przygotowanie
    Edycja notatek           :done, a1, 2026-05-15, 1d
    Sprawdzenie localhost    :done, a2, after a1, 1d
    section GitHub
    Commit zmian             :active, a3, after a2, 1d
    Push na GitHub           :a4, after a3, 1d
    section Publikacja
    GitHub Actions           :a5, after a4, 1d
    Aktualizacja strony      :milestone, a6, after a5, 0d
```
````

### Wynik

```mermaid
gantt
    title Aktualizacja i publikacja notatek
    dateFormat YYYY-MM-DD
    section Przygotowanie
    Edycja notatek           :done, a1, 2026-05-15, 1d
    Sprawdzenie localhost    :done, a2, after a1, 1d
    section GitHub
    Commit zmian             :active, a3, after a2, 1d
    Push na GitHub           :a4, after a3, 1d
    section Publikacja
    GitHub Actions           :a5, after a4, 1d
    Aktualizacja strony      :milestone, a6, after a5, 0d
```

## Zasada

Diagram Gantta zaczynam od słowa `gantt`, potem ustawiam `title`, `dateFormat`, sekcje i zadania. Mermaid pozwala oznaczać zadania jako `done`, `active` oraz `milestone`. [web:688][web:691]