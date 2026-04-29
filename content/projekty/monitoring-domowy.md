---
title: Domowy monitoring usług i urządzeń
description: Podejście do monitoringu usług, hostów i urządzeń sieciowych w homelabie.
---

## Zakres

Chcę mieć prosty, użyteczny monitoring domowej infrastruktury:
- hostów,
- kontenerów,
- usług,
- urządzeń sieciowych,
- NAS-a.

## Narzędzia

Obecnie najbliższe mi podejście to:
- Grafana do wizualizacji,
- Prometheus do zbierania metryk,
- Telegraf tam, gdzie pasuje,
- SNMP dla wybranych urządzeń.

## Priorytety

Najważniejsze metryki:
- dostępność usług,
- użycie CPU i RAM,
- miejsce na dyskach,
- podstawowy ruch sieciowy,
- stan kluczowych urządzeń.

## Notatka robocza

Monitoring ma być praktyczny, a nie „ładny dla samego dashboardu”. Najpierw sygnały naprawdę użyteczne, dopiero potem kosmetyka.