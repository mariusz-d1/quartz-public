---
title: OpenWRT - aktualizacja wersji
description: Notatka o aktualizacji firmware OpenWRT oraz kontroli DHCP i DNS po zmianie wersji.
tags:
  - homelab
  - openwrt
  - firmware
  - router
  - dhcp
  - dns
---

# OpenWRT - aktualizacja wersji

Ta notatka dotyczy aktualizacji firmware OpenWRT na routerze, który w mojej sieci odpowiada za kluczowe elementy działania LAN. To nie jest tylko zwykły upgrade systemu, bo od poprawnej pracy routera zależą DHCP, podstawowe zasady sieci oraz sposób rozdawania DNS klientom. [file:661]

## Dlaczego aktualizacja jest ważna

Router z OpenWRT jest punktem, w którym spinają się:
- DHCP,
- podstawowe zasady sieci,
- dystrybucja adresów DNS do klientów. [file:661]

Przy usługach takich jak Pi-hole to właśnie konfiguracja DHCP i DNS na routerze decyduje, czy całość działa przewidywalnie. Po aktualizacji trzeba więc patrzeć nie tylko na to, czy router wstał, ale też czy cała sieć zachowuje się tak jak wcześniej. [file:661]

## Cel tej notatki

Celem tej notatki jest zapisanie:
- jak sprawdzić, czy są aktualizacje,
- jak przygotować się do zmiany wersji,
- co sprawdzić po aktualizacji,
- jakie ustawienia DHCP i DNS muszą zostać zweryfikowane. [file:661]

## Przed aktualizacją

Przed aktualizacją firmware warto spisać:
- aktualną wersję OpenWRT,
- model routera,
- sposób aktualizacji,
- czy konfiguracja ma zostać zachowana,
- główne ustawienia DHCP,
- podstawowy i zapasowy DNS,
- najważniejsze reguły sieciowe i przekierowania portów.

Dobrze też wykonać kopię konfiguracji przed zmianą wersji, żeby w razie problemów mieć prostą drogę powrotu.

## Sprawdzenie czy są aktualizacje

Pierwszy krok to ustalenie, czy dla używanej wersji i modelu routera jest dostępny nowszy firmware. Na tym etapie warto sprawdzić:
- obecną wersję systemu,
- zgodność obrazu z urządzeniem,
- ewentualne uwagi do nowej wersji,
- czy aktualizacja jest mała i bezpieczna, czy może wymaga większej ostrożności.

## Założenia po aktualizacji

Po aktualizacji router powinien:
- wrócić z poprawnym adresem IP,
- nadal rozdawać adresy z DHCP,
- przekazywać klientom właściwy DNS,
- zachować dostęp do panelu administracyjnego,
- nie zgubić najważniejszych ustawień sieciowych.

W praktyce najważniejsze jest to, żeby po restarcie nie powstał chaos w DHCP i DNS.

## Co sprawdzić po aktualizacji

Po zmianie wersji warto przejść krótką checklistę:

- Czy panel OpenWRT otwiera się poprawnie.
- Czy router odpowiada pod swoim stałym adresem.
- Czy klient dostaje poprawny adres z DHCP.
- Czy klient dostaje poprawny DNS.
- Czy działa rozwiązywanie nazw lokalnych i zewnętrznych.
- Czy internet działa na komputerze i telefonie.
- Czy Pi-hole lub inny główny DNS nadal działa zgodnie z planem.
- Czy zapasowy DNS nie przejął ruchu w niepożądany sposób.
- Czy reguły firewalla i przekierowania portów nadal działają.

## Testy po zmianach

Docelowo chcę tu dopisać checklistę testów po aktualizacji, ale minimalny zestaw obejmuje:
1. odnowienie dzierżawy DHCP na komputerze,
2. sprawdzenie adresu bramy i DNS,
3. test otwierania stron internetowych,
4. test wejścia na lokalne usługi po IP i po nazwie,
5. test działania usług zależnych od DNS.

## Ryzyka

Największy problem po aktualizacji routera to niekoniecznie całkowity brak internetu, ale częściowa awaria. Taki stan bywa trudniejszy do wykrycia, bo część usług działa poprawnie, a część nie — na przykład internet działa po IP, ale DNS jest rozdawany źle albo niezgodnie z planem.

## Do spisania

Docelowo chcę tu dopisać:
- finalne ustawienia DHCP,
- wariant główny i zapasowy DNS,
- checklistę testów po zmianach,
- wersję przed aktualizacją i po aktualizacji,
- informację, czy konfiguracja została zachowana,
- ewentualne poprawki wymagane po restarcie.

## Wnioski

Aktualizacja OpenWRT to w praktyce aktualizacja centralnego punktu domowej sieci. Jeśli router odpowiada za DHCP i DNS, to po każdej zmianie wersji trzeba sprawdzić nie tylko sam system, ale też zachowanie klientów i usług zależnych od routingu oraz rozwiązywania nazw. [file:661]