---
title: Pi-hole w układzie główny plus backup
description: Koncepcja redundancji DNS w domu z głównym Pi-hole i zapasową instancją.
---

## Założenie

Docelowo chcę utrzymywać dwa serwery DNS filtrujące:
- główny Pi-hole,
- zapasowy Pi-hole.

## Pomysł

Układ podstawowy:
- Raspberry Pi 4 jako główna instancja,
- QNAP jako backup,
- oba urządzenia podłączone do UPS,
- DHCP po stronie OpenWRT.

## Dlaczego tak

Taki układ daje prostotę i sensowną odporność na awarie jednego hosta bez przesadnego komplikowania środowiska.

## Do dopracowania

- dokładna konfiguracja DHCP option 6,
- zachowanie klientów przy awarii głównego DNS,
- sposób aktualizacji i backupu konfiguracji.