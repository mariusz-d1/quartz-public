---
title: Git i publikacja Quartz na GitHub
description: Szybka ściąga do sprawdzania zmian, commitowania i wypychania Quartz na GitHub.
tags:
  - techniczne
  - quartz
  - git
  - github
---

# Git i publikacja Quartz na GitHub

To jest moja szybka ściąga do publikacji zmian z Quartz na GitHuba.

## Kolejność pracy

Najpierw robię zmiany w notatkach, potem sprawdzam je lokalnie na localhost, a dopiero na końcu wysyłam na GitHuba.

## Sprawdzenie statusu zmian

W terminalu VS Code wpisuję:

```powershell
git status
```

Ta komenda pokazuje, które pliki zostały zmienione, dodane albo czekają na commit.

## Dodanie zmian

Jeśli wszystko wygląda dobrze, dodaję zmiany:

```powershell
git add .
```

## Commit

Potem zapisuję zmiany commitem:

```powershell
git commit -m "Dodanie i poprawki notatek w Quartz"
```

Lepiej pisać krótki, konkretny opis, np.:
- `git commit -m "Dodanie notatki o aktualizacji OpenWRT"`
- `git commit -m "Poprawki w folderze homelab"`
- `git commit -m "Dodanie technicznych notatek o Quartz"`

## Aktualizacja gałęzi lokalnej

Przed pushowaniem dobrze pobrać najnowsze zmiany z repozytorium:

```powershell
git pull --rebase origin main
```

## Wysłanie zmian

Na końcu wypycham zmiany:

```powershell
git push origin main
```

## Co dzieje się dalej

Po pushu GitHub uruchamia workflow i buduje stronę Quartz automatycznie, jeśli repo jest podpięte pod GitHub Pages i Actions. To typowy sposób publikacji Quartz na GitHub Pages. [web:406][web:485]

## Szybka wersja

Najczęściej używam tego zestawu:

```powershell
git status
git add .
git commit -m "Opis zmian"
git pull --rebase origin main
git push origin main
```