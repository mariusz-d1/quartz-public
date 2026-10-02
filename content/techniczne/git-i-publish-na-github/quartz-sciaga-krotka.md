## Quartz – szybka ściąga

- Po większych zmianach w linkach albo strukturze folderów czasem trzeba zrestartować Quartza.
- Jeśli localhost pokazuje coś dziwnego, najpierw: `Ctrl + C`, potem `npx quartz build --serve`.
- Nie wkładać wikilinków do backticków, bo Quartz potraktuje je jak kod, a nie link.
- Lepiej używać prostych wikilinków typu `[[porzadki-i-migracje]]` niż ścieżek z `../`.
- `index.md` działa jako strona wejściowa folderu.
- `title:` w frontmatterze może dublować `# H1` w treści.
- Po każdej zmianie sprawdzić localhost przed `git add`, `commit` i `push`.
- Jeśli w VS Code wygląda dobrze, a na localhost źle, sprawdzić: linki, backticki, H1 i restart Quartza.
## Lokalny podgląd Quartz

W katalogu głównym repozytorium Quartz uruchom terminal PowerShell i wpisz:

```powershell
npx quartz build --serve
```

Następnie otwórz w przeglądarce:

```text
http://localhost:8080
```

Quartz zbuduje stronę z plików Markdown i uruchomi lokalny podgląd dostępny wyłącznie na tym komputerze.

### Automatyczne odświeżanie

Tryb `--serve` obserwuje zmiany w plikach. Wystarczy zapisać notatkę `.md` w katalogu:

```text
content\
```

a Quartz powinien automatycznie przebudować stronę i odświeżyć podgląd w przeglądarce.

### Zatrzymanie lokalnego serwera

Aby zakończyć działanie podglądu, przejdź do terminala, w którym działa Quartz, i naciśnij:

```text
Ctrl + C
```

### Typowy cykl pracy

```text
Edycja notatki → Ctrl+S → kontrola na localhost:8080 → git add / commit / push → publikacja na GitHub Pages
```
