---
title: Raspberry Pi 4 jako główny host usług
description: Domowy serwer na Raspberry Pi 4 — sprzęt, automatyka, monitoring i doświadczenia z utrzymania.
date: 2026-04-30
lastmod: 2026-10-31
tags:
  - homelab
  - raspberry-pi
  - docker
  - monitoring
---

Raspberry Pi 4 pełni u mnie rolę stale działającego serwera usług domowych. Łączy automatykę, zbieranie metryk, przeglądanie logów i kilka narzędzi pomocniczych. To jednocześnie użytkowy element domowej infrastruktury i miejsce do nauki administracji Linuksem oraz kontenerami.

Najważniejsze założenia pozostają proste: przewidywalne działanie, niski pobór energii, możliwość zdalnej administracji i łatwość odtworzenia środowiska po awarii. Niski pobór energii jest założeniem projektu — nie mam tu jeszcze zestawienia pomiarów całego zestawu.

> [!info] Zakres i aktualność
> Opis opiera się na lokalnej dokumentacji i inwentaryzacji z 29 października 2026 r. Nie jest bieżącym raportem dostępności usług ani instrukcją odtworzenia całego serwera.

## Sprzęt i system

| Element | Zastosowane rozwiązanie |
| --- | --- |
| Komputer | Raspberry Pi 4 Model B |
| Pamięć RAM | 8 GB |
| Architektura | ARM64 |
| System | Ubuntu 24.04 LTS |
| Nośnik systemowy | SSD NVMe podłączony przez USB 3.0 |
| Obudowa / adapter dysku | Argon NVMe |
| System plików partycji głównej | ext4 |
| Uruchamianie aplikacji | Docker i Docker Compose |

System i dane usług znajdują się na SSD. Określenie „NVMe” dotyczy samego dysku — w tym zestawie komunikacja z Raspberry Pi odbywa się przez mostek USB, a nie przez bezpośrednie połączenie PCIe.

Podczas inwentaryzacji pozostawał duży zapas wolnego miejsca. To jednak tylko jeden z parametrów do obserwowania: osobno trzeba kontrolować przyrost logów i danych monitoringu.

## Jakie zadania realizuje serwer?

| Obszar | Narzędzia | Rola |
| --- | --- | --- |
| Automatyka domowa | Home Assistant, Domoticz | Integracja urządzeń i obsługa automatyki |
| Komunikacja IoT | Mosquitto | Broker MQTT pośredniczący w wymianie komunikatów |
| Metryki | Prometheus | Zbieranie i przechowywanie szeregów czasowych |
| Prezentacja danych | Grafana | Wykresy i pulpity monitoringu |
| Monitoring systemu i kontenerów | Node Exporter, cAdvisor | Metryki hosta oraz kontenerów |
| Logi | Loki, Promtail, rsyslog | Zbieranie i przeglądanie wybranych logów |
| Obserwacja sieci | NetAlertX | Obserwacja obecności urządzeń w sieci |
| Monitoring infrastruktury | Zabbix | Osobne środowisko monitoringu |
| Administracja | Portainer | Interfejs zarządzania kontenerami |
| Dokumentacja lokalna | DokuWiki | Zaplecze dokumentacyjne |
| Usługi pomocnicze | nginx, MariaDB | Reverse proxy i baza danych dla aplikacji |

Obecność narzędzia w zestawieniu oznacza jego rolę w środowisku. Nie potwierdza kompletności wszystkich integracji ani automatyzacji. Część rozwiązań ma charakter laboratoryjny i jest rozwijana stopniowo.

## Monitoring w praktyce

Prometheus zbiera metryki z eksporterów, a Grafana przedstawia je na pulpitach. Dzięki temu mogę obserwować obciążenie serwera, wykorzystanie zasobów i dane wybranych urządzeń.

### Host i kontenery

Node Exporter dostarcza metryki systemu, a cAdvisor — kontenerów. Te dwa poziomy obserwacji pomagają odróżnić problem całego hosta od problemu jednej aplikacji.

### Drukarka

Ciekawym dodatkiem jest własny eksporter dla HP Officejet 6500. Pobiera dane z interfejsu urządzenia i udostępnia je Prometheusowi. Pozwala to prezentować w Grafanie między innymi liczniki wydrukowanych stron i zgłaszane poziomy tuszu.

Dla starszej drukarki jest to użyteczne uzupełnienie jej panelu WWW: wybrane informacje trafiają do wspólnego pulpitu monitoringu.

### Metryki i logi

Metryki pokazują, co zmienia się w czasie. Logi pomagają ustalić, jakie zdarzenie mogło wywołać zmianę. W tym środowisku wybrane komunikaty urządzeń ESP Easy trafiają przez syslog do lokalnego odbiornika, a następnie do Loki. Grafana służy także do ich przeglądania.

## Kontenery w codziennym użytkowaniu

Docker pozwala mi uruchamiać na jednym Raspberry Pi wiele usług o różnych zadaniach. Każda aplikacja ma własne środowisko i zależności, a Docker Compose opisuje sposób jej uruchomienia oraz powiązania z pozostałymi elementami.

Kontenery współdzielą zasoby i jądro systemu gospodarza. Awaria hosta lub jego dysku może więc przerwać działanie całego zestawu. Podział aplikacji na kontenery ułatwia administrację, ale sam w sobie nie zapewnia wysokiej dostępności.

### Podział według zadań

Usługi organizuję w projekty Compose. Powiązane elementy, takie jak aplikacja i jej baza danych, można w ten sposób opisać i utrzymywać razem. W środowisku występują zarówno usługi wykorzystywane na co dzień, jak i osobne projekty laboratoryjne.

Główne grupy to automatyka domowa, monitoring, obsługa logów i narzędzia pomocnicze opisane w tabeli wyżej. Osobne środowisko Zabbixa pozwala rozwijać kolejny sposób obserwacji infrastruktury.

Projekty nadal korzystają ze wspólnego procesora, pamięci, dysku i połączenia sieciowego. Przy dodawaniu aplikacji trzeba więc brać pod uwagę obciążenie całego Raspberry Pi.

### Obraz, kontener i dane aplikacji

W dokumentacji rozróżniam trzy elementy:

| Element | Znaczenie |
| --- | --- |
| Obraz | Pakiet aplikacji i zależności używany do tworzenia kontenera |
| Kontener | Uruchomiony lub zatrzymany egzemplarz utworzony z obrazu |
| Dane trwałe | Ustawienia i zawartość aplikacji zachowywane poza zapisywalną warstwą kontenera |

Dane trwałe wielu aplikacji znajdują się w katalogach podłączanych z hosta, czyli bind mountach. W środowisku występują również wolumeny zarządzane przez Dockera. Oba rodzaje przechowywania danych wymagają uwzględnienia w dokumentacji i planie kopii zapasowych.

Samo zachowanie obrazu lub pliku Compose nie wystarcza do odzyskania historii pomiarów, ustawień aplikacji czy zawartości bazy danych. Trwałość danych poza kontenerem również nie zastępuje backupu.

### Organizacja konfiguracji i danych

Przy dokumentowaniu i planowaniu odtworzenia rozróżniam:

- definicje usług i konfigurację;
- dane trwałe aplikacji;
- bazy danych;
- metryki i logi;
- materiały historyczne oraz projekty wstrzymane.

Ten podział pomaga określić, co wymaga kopii, a co można odtworzyć z konfiguracji. Bazy danych wymagają dodatkowo metody zapewniającej spójność kopii.

### Projekty testowe i wstrzymane

Zatrzymany kontener może być pozostałością próby, zadaniem jednorazowym albo elementem projektu, do którego planuję wrócić. Sam jego status nie jest podstawą do usunięcia.

Przed zmianą ustalam przeznaczenie projektu, jego zależności oraz miejsce przechowywania danych. Materiały historyczne zachowuję do czasu wyjaśnienia ich roli.

### Aktualizacje i możliwość powrotu

Przed aktualizacją trzeba sprawdzić wybraną wersję obrazu, zgodność z ARM64 oraz wymagania aplikacji. Częścią przygotowania jest zabezpieczenie konfiguracji i danych.

Nowa wersja aplikacji może zmienić format danych lub strukturę bazy. W takiej sytuacji samo uruchomienie starszego obrazu nie musi wystarczyć do cofnięcia aktualizacji. Sposób powrotu należy przygotować przed zmianą.

## Czego nauczyła mnie eksploatacja?

### Uruchomiony kontener nie oznacza sprawnej usługi

Status `Up` informuje o działającym procesie kontenera. Nie dowodzi, że aplikacja otrzymuje poprawne dane albo wykonuje swoje zadania.

Podobnie odpowiedź endpointu metryk potwierdza możliwość jego odczytu, ale nie musi oznaczać, że docelowe urządzenie jest skutecznie monitorowane. Sprawdzam również obecność oczekiwanych metryk i aktualność danych. Przykładowo dostępny panel Grafany potwierdza działanie interfejsu, ale dopiero świeże pomiary na wykresie pomagają potwierdzić działanie całego toru zbierania danych.

### Healthcheck też wymaga sprawdzenia

Test zdrowia musi pasować do zawartości obrazu i rzeczywistej funkcji aplikacji. Wadliwy test może zgłaszać awarię poprawnie działającej usługi. Z kolei zbyt powierzchowny test może nie wykryć problemu z jej podstawowym zadaniem.

### Architektura obrazu ma znaczenie

Na Raspberry Pi sprawdzam zgodność obrazu z ARM64. Sama nazwa aplikacji ani tag obrazu nie wystarczają do potwierdzenia, że wybrany wariant uruchomi się na tym hoście.

### Logi potrzebują kontroli

Nawet niewielka usługa może z czasem wygenerować dużo logów. Przy jej utrzymaniu trzeba uwzględnić zakres zapisywanych komunikatów, rotację i okres przechowywania danych.

### Start procesu i gotowość to różne etapy

Aplikacja zależna od bazy danych może wymagać oczekiwania na gotowość bazy. Sprawdzam również zachowanie polityk restartu po ręcznym zatrzymaniu kontenerów. Test uruchomienia obejmuje więc także działanie aplikacji, a nie wyłącznie listę procesów.

## Kopie zapasowe i odtwarzanie

Celem jest możliwość odtworzenia konfiguracji oraz najważniejszych danych usług. Pełna procedura backupu i odtwarzania pozostaje obszarem do dopracowania i przetestowania.

Nie traktuję działającego serwera ani samego istnienia archiwum jako potwierdzenia skutecznego backupu. Potrzebne są kontrola zawartości kopii i próba odtworzenia. Dla baz danych należy dobrać metodę zapewniającą spójność zapisu.

Szczegółowe lokalizacje danych, harmonogramy i instrukcje serwisowe prowadzę w dokumentacji prywatnej.

## Kierunki dalszych prac

- Dopracowanie kopii zapasowych i sprawdzenie odtwarzania usług.
- Ujednolicenie kontroli gotowości aplikacji i ich zależności.
- Rozwój pulpitów oraz integracji monitoringu.
- Kontrola przyrostu logów i danych historycznych.
- Uporządkowanie wersjonowania obrazów i kontrolowanych aktualizacji.
- Rozwijanie lokalnego panelu HMI do wygodnego podglądu na tablecie.

## Dokumentacja publiczna i prywatna

Tutaj opisuję budowę środowiska, przeznaczenie narzędzi i wnioski z pracy. Dokładna adresacja, identyfikatory sprzętu, dane dostępowe, konfiguracje administracyjne i wyniki diagnostyki pozostają w prywatnych notatkach.

Taki podział pozwala dzielić się doświadczeniami bez publikowania szczegółowej mapy domowej infrastruktury.
