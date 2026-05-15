---
title: Mermaid w Quartz
description: Szybka ściąga do diagramów Mermaid w notatkach Quartz.
tags:
  - techniczne
  - mermaid
  - quartz
---

# Mermaid w Quartz

Mermaid pozwala dodawać diagramy bezpośrednio w Markdown przez blok kodu oznaczony jako `mermaid`.

## Najprostszy diagram

### Kod

````md
```mermaid
flowchart LR
    A[Start] --> B[Edycja notatki]
    B --> C[Podgląd localhost]
    C --> D[Commit]
    D --> E[Push na GitHub]
```
````

### Wynik

```mermaid
flowchart LR
    A[Start] --> B[Edycja notatki]
    B --> C[Podgląd localhost]
    C --> D[Commit]
    D --> E[Push na GitHub]
```

## Diagram sekwencji

### Kod

````md
```mermaid
sequenceDiagram
    participant U as Użytkownik
    participant V as VS Code
    participant Q as Quartz
    participant G as GitHub

    U->>V: Edytuje notatkę
    V->>Q: Zapis pliku
    Q->>U: Podgląd localhost
    U->>G: Push zmian
```
````

### Wynik

```mermaid
sequenceDiagram
    participant U as Użytkownik
    participant V as VS Code
    participant Q as Quartz
    participant G as GitHub

    U->>V: Edytuje notatkę
    V->>Q: Zapis pliku
    Q->>U: Podgląd localhost
    U->>G: Push zmian
```

## Zasada

Kod Mermaid wpisuję zawsze między potrójne backticki i poprzedzam słowem `mermaid`. Jeśli chcę pokazać sam kod jako przykład, zamykam go w osobnym bloku z czterema backtickami, a niżej dodaję właściwy blok renderujący diagram. [web:675][web:673]

## Najkrótszy wzór

### Kod

````md
```mermaid
flowchart TD
    A --> B
```
````

### Wynik

```mermaid
flowchart TD
    A --> B
```