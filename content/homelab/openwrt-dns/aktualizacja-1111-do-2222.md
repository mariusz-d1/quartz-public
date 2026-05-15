---
title: OpenWRT - aktualizacja wersji 11111 do 22222
description: Mój zapis z aktualizacji firmware OpenWRT i kontroli działania sieci po restarcie routera.
tags:
  - homelab
  - openwrt
  - firmware
  - router
  - dhcp
  - dns
---

# OpenWRT - aktualizacja wersji

Zabrałem się za aktualizację OpenWRT, bo router w mojej sieci nie jest tylko „pudełkiem od internetu”, ale faktycznym punktem centralnym całego LAN-u. To przez niego przechodzą podstawowe zasady działania sieci, DHCP i dystrybucja DNS, więc każda zmiana firmware ma u mnie większy ciężar niż zwykły upgrade pojedynczej usługi.

## Dlaczego w ogóle to ruszałem

Przy usługach takich jak Pi-hole albo innych elementach opartych o własny DNS, router ma kluczowe znaczenie. Jeśli po aktualizacji coś się rozjedzie, to problem nie musi wyglądać spektakularnie — czasem internet „niby działa”, ale klienci dostają zły DNS, nazwy lokalne przestają się rozwiązywać albo część urządzeń zaczyna zachowywać się inaczej niż przed zmianą. [file:661]

Dlatego potraktowałem tę aktualizację nie jako kliknięcie „upgrade”, tylko jako zmianę w newralgicznym punkcie infrastruktury domowej. [file:661]

## Co chciałem osiągnąć

Celem było bezpieczne podniesienie wersji OpenWRT bez rozwalenia tego, co już działało dobrze. Najważniejsze było dla mnie zachowanie porządku w:
- DHCP,
- DNS,
- dostępie do panelu routera,
- ogólnej przewidywalności sieci po restarcie.

## Co spisałem przed zmianą

Zanim ruszyłem z aktualizacją, warto było mieć pod ręką kilka podstawowych informacji:
- jaka wersja działa obecnie,
- jaki to dokładnie model routera,
- czy konfiguracja ma zostać zachowana,
- jakie są ustawienia DHCP,
- jaki jest główny i zapasowy DNS,
- czy są jakieś ważne przekierowania portów lub niestandardowe reguły.

To jest ten moment, w którym kilka minut notowania oszczędza później dużo niepotrzebnego kombinowania.

## Sam pomysł na aktualizację

Założenie było proste: zrobić upgrade tak, żeby po restarcie router nie tylko wstał, ale też zachował logikę działania całej sieci. W praktyce interesowało mnie nie tylko to, czy da się wejść do LuCI, ale też czy klienci nadal dostają poprawne ustawienia i czy DNS działa dokładnie tak, jak wcześniej.

## Co sprawdzam po restarcie

Po aktualizacji firmware przechodzę sobie krótką checklistę:

- Czy router odpowiada pod swoim adresem IP.
- Czy panel administracyjny działa poprawnie.
- Czy komputer dostaje adres z DHCP.
- Czy komputer dostaje właściwy DNS.
- Czy działają strony internetowe.
- Czy działają nazwy lokalne i usługi w LAN.
- Czy Pi-hole albo główny resolver dalej pracują zgodnie z planem.
- Czy nie zniknęły ważne ustawienia sieciowe.

Dopiero kiedy to wszystko się zgadza, uznaję aktualizację za zamkniętą.

## Największe ryzyko

Najbardziej zdradliwy nie jest całkowity brak internetu, tylko częściowy bałagan. To jest ten scenariusz, w którym wszystko wygląda prawie dobrze, ale:
- jedno urządzenie dostaje inny DNS,
- część usług lokalnych działa tylko po IP,
- coś przestaje działać po nazwie,
- albo sieć działa „niby normalnie”, ale już nie tak przewidywalnie jak wcześniej.

Właśnie dlatego po aktualizacji warto testować nie tylko internet, ale cały kontekst działania sieci domowej.

## Co chcę tu jeszcze dopisać

Ta notatka ma być dla mnie wzorcem, więc docelowo chcę jeszcze uzupełniać w niej:
- wersję przed aktualizacją i po aktualizacji,
- informację, czy konfiguracja została zachowana,
- ewentualne poprawki robione już po restarcie,
- finalne ustawienia DHCP,
- wariant głównego i zapasowego DNS,
- checklistę testów po zmianach.

## Wniosek po takim podejściu

Aktualizacja OpenWRT to dla mnie nie tylko zmiana firmware, ale kontrola spójności całej sieci. Router jest zbyt ważnym elementem, żeby traktować go jak zwykłą usługę, więc każda aktualizacja powinna kończyć się nie tylko sukcesem systemowym, ale też potwierdzeniem, że DHCP, DNS i codzienne działanie LAN-u pozostały pod kontrolą. [file:661]