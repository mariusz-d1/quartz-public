---
title: OpenWRT, DHCP i porządek w DNS
description: Notatka o roli routera w rozdzielaniu DNS i organizacji sieci lokalnej.
---

## Rola routera

Router z OpenWRT jest punktem, w którym spinają się:
- DHCP,
- podstawowe zasady sieci,
- dystrybucja adresów DNS do klientów.

## Dlaczego to ważne

Przy usługach takich jak Pi-hole to właśnie konfiguracja DHCP i DNS na routerze decyduje, czy całość działa przewidywalnie.

## Do spisania

Docelowo chcę tu dopisać:
- finalne ustawienia DHCP,
- wariant główny i zapasowy DNS,
- checklistę testów po zmianach.