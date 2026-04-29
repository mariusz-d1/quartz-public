---
title: Usługi dockerowe w domu
description: Krótka notatka o podejściu do uruchamiania usług w Dockerze.
---

## Podejście

Jeśli usługa dobrze mieści się w kontenerze, zwykle wolę uruchomić ją właśnie w Dockerze.

## Korzyści

Najważniejsze plusy:
- powtarzalność,
- prostsze aktualizacje,
- łatwiejsze przenoszenie,
- czytelniejsze odtwarzanie środowiska.

## Zasada

Każda nowa usługa powinna mieć przynajmniej:
- opis celu,
- porty,
- wolumeny,
- zależności,
- plan backupu.