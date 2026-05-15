---
title: Mermaid - architektura homelabu
description: Przykład diagramu architektury homelabu w Mermaid z pokazaniem kodu i wyniku.
tags:
  - techniczne
  - mermaid
  - quartz
  - homelab
  - architektura
---

# Mermaid - architektura homelabu

To przykład prostego diagramu architektury homelabu w Mermaid. Taki układ dobrze nadaje się do opisu routera, NAS-a, Raspberry Pi i usług monitoringu.

## Wersja architektury

### Kod

````md
```mermaid
flowchart LR
    Internet[Internet] --> Router[OpenWRT Router]
    Router --> DNS[Pi-hole / DNS]
    Router --> QNAP[QNAP TS-431P]
    Router --> RPI[Raspberry Pi 4]
    Router --> PC[Mini PC / Ubuntu]

    RPI --> HA[Home Assistant]
    PC --> Prom[Prometheus]
    PC --> Graf[Grafana]
    QNAP --> Files[Pliki i backup]
```
````

### Wynik

```mermaid
flowchart LR
    Internet[Internet] --> Router[OpenWRT Router]
    Router --> DNS[Pi-hole / DNS]
    Router --> QNAP[QNAP TS-431P]
    Router --> RPI[Raspberry Pi 4]
    Router --> PC[Mini PC / Ubuntu]

    RPI --> HA[Home Assistant]
    PC --> Prom[Prometheus]
    PC --> Graf[Grafana]
    QNAP --> Files[Pliki i backup]
```

## Zasada

Do opisywania architektury homelabu w Quartz najbezpieczniej używać `flowchart`, bo jest prosty, czytelny i renderuje się stabilnie.

## Kiedy używać

Taki diagram przydaje się, gdy chcę szybko pokazać:
- główne urządzenia w sieci,
- zależności między nimi,
- gdzie działają konkretne usługi,
- które elementy odpowiadają za monitoring, DNS albo storage.

## Własny wariant

Ten przykład można łatwo rozbudować o kolejne elementy, na przykład:
- dodatkowy NAS,
- osobny serwer backupu,
- Home Assistant,
- Node-RED,
- DokuWiki,
- Homepage,
- Pi-hole zapasowy.

## Minimalny wzór

### Kod

````md
```mermaid
flowchart LR
    A[Router] --> B[NAS]
    A --> C[Raspberry Pi]
    C --> D[Monitoring]
```
````

### Wynik

```mermaid
flowchart LR
    A[Router] --> B[NAS]
    A --> C[Raspberry Pi]
    C --> D[Monitoring]
```