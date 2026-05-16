---
title: Techniczne
description: Notatki techniczne o Quartz, VS Code, GitHub, Markdown i Mermaid.
---

# Techniczne

Zbiór szybkich notatek pomocniczych do edycji, podglądu i publikacji treści w Quartz.

# Szybka ściąga

Do codziennego użycia zapamiętaj ten zestaw:

powershell
- npx quartz build --serve

Uwaga: przy komendach typu --serve wpisywać myślniki ręcznie, bo po wklejeniu może wejść en dash / em dash i npm zwraca błąd non-ascii dash.

potem w przeglądarce:


http://localhost:8080/

a po sprawdzeniu:

powershell

- git status

- git add .

- git commit -m "Opis zmian"

- git pull --rebase origin main

- git push origin main

Quartz lokalnie działa przez --serve na porcie 8080, a po pushu GitHub Actions może automatycznie zbudować i opublikować stronę.

## Spis

- [VS Code i podgląd Quartz na localhost](./vscode-i-podglad-localhost/)
- [Git i publikacja Quartz na GitHub](./git-i-publish-na-github/)
- [Markdown - podstawy do Quartz](./markdown-podstawy/)
- [Mermaid w Quartz](./mermaid-w-quartz/)
- [Mermaid - gantt w Quartz](./mermaid-gantt/)
- [Mermaid - architektura homelabu](./mermaid-architektura-homelabu/)
- [Mermaid - edycja notatki, localhost i GitHub](./mermaid-flow-notatka-localhost-git/)