## Quartz – szybka ściąga

- Po większych zmianach w linkach albo strukturze folderów czasem trzeba zrestartować Quartza.
- Jeśli localhost pokazuje coś dziwnego, najpierw: `Ctrl + C`, potem `npx quartz build --serve`.
- Nie wkładać wikilinków do backticków, bo Quartz potraktuje je jak kod, a nie link.
- Lepiej używać prostych wikilinków typu `[[porzadki-i-migracje]]` niż ścieżek z `../`.
- `index.md` działa jako strona wejściowa folderu.
- `title:` w frontmatterze może dublować `# H1` w treści.
- Po każdej zmianie sprawdzić localhost przed `git add`, `commit` i `push`.
- Jeśli w VS Code wygląda dobrze, a na localhost źle, sprawdzić: linki, backticki, H1 i restart Quartza.
