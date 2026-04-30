---
title: Publikacja notatek przez Quartz i GitHub Pages
description: Jak uruchomiłem publiczną stronę z notatkami na Quartz 4 i GitHub Pages.
---

## Cel

Chciałem uruchomić prostą, publiczną stronę do publikowania wybranych notatek technicznych.

Założenia:
- treść piszę w Markdown,
- repozytorium trzymam na GitHubie,
- publikacja ma działać automatycznie po pushu,
- rozwiązanie ma być lekkie i proste w utrzymaniu.

## Stos

- Quartz 4
- GitHub Pages
- GitHub Actions
- Markdown

## Efekt

Strona działa publicznie i publikuje zawartość katalogu `content/`.

## Wnioski

Najważniejsze było odróżnienie workflowów technicznych repo od właściwego workflowu publikacji na GitHub Pages.

Dodatkowo build wymagał odpowiedniej wersji Node.js zgodnej z wymaganiami Quartza.