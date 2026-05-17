---
title: Backup DokuWiki
---

# Backup DokuWiki

## Cel

Przed aktualizacją template, pluginów lub większą zmianą konfiguracji należy wykonać kopię zapasową instalacji DokuWiki.

## Co backupować

Najważniejsze elementy:
- cały katalog instalacji DokuWiki
- konfigurację
- dane wiki
- pluginy
- template

## Minimalny backup

Najbezpieczniej skopiować cały katalog DokuWiki z hostingu.

Jeśli potrzebny jest szybki backup minimalny, szczególnie ważne są katalogi i pliki odpowiedzialne za:
- treść wiki
- konfigurację
- zainstalowane pluginy
- aktywny template

## Sposób wykonania

### Opcja 1 — panel hostingu

1. Zalogować się do panelu cyber_Folks.
2. Otworzyć menedżer plików.
3. Odnaleźć katalog instalacji DokuWiki.
4. Spakować cały katalog do pliku `.zip`.
5. Pobrać archiwum na komputer.

### Opcja 2 — FTP

1. Połączyć się przez FTP.
2. Pobrać cały katalog instalacji DokuWiki na komputer.
3. Zachować kopię lokalną przed zmianami.

## Kiedy wykonano

- [ ] backup przed aktualizacją sprintdoc
- [ ] backup przed zmianą sidebara
- [ ] backup po ustabilizowaniu konfiguracji

## Uwagi

Przed przełączeniem template z `roundbox` na `sprintdoc` wykonać świeży backup.

## Historia backupów

- 2026-05-17 – pełny ZIP katalogu `dokuwiki` w `public_html`, nazwa: `dokuwiki-2026-05-17.zip`, kopia lokalna: do pobrania po ogarnięciu hasła FTP.
