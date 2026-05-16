# Quartz – pułapki i dobre praktyki przy notatkach

Poniższa notatka nadaje się do wklejenia do folderu **„Git i publikacja Quartz na GitHub”** albo **„Markdown – podstawy do Quartz”**. Zbiera kilka rzeczy, które wyszły przy pracy lokalnie na localhost.

## Quartz czasem wymaga restartu

Przy zwykłej edycji markdowna Quartz zwykle odświeża stronę automatycznie. Czasem jednak po zmianie linków, nazw plików, struktury folderów albo `index.md` podgląd nie odświeża się poprawnie i warto zrestartować serwer lokalny:

```bash
Ctrl + C
npx quartz build --serve
```

Jeśli localhost pokazuje stary albo niepełny widok, restart Quartza jest pierwszą rzeczą do sprawdzenia.

## Nie wkładać wikilinków do backticków

To jest błędne:

```md
`[[porzadki-i-migracje|Porządki i migracje]]`
```

Backticki robią z tego **kod**, a nie aktywny link.

Poprawnie:

```md
[[porzadki-i-migracje|Porządki i migracje]]
```

Jeśli link ma działać w Quartz, nie może być zapisany jako inline code.

## Uważać na ścieżki typu `../`

W zwykłym markdownzie lub systemie plików człowiek naturalnie myśli o ścieżkach względnych typu:

```md
[[../porzadki-i-migracje|Porządki i migracje]]
```

W Quartz lepiej trzymać się prostszych wikilinków:

```md
[[porzadki-i-migracje|Porządki i migracje]]
```

albo bardziej jednoznacznych nazw notatek, jeśli istnieje ryzyko duplikatów nazw.

## `title` i `# H1` mogą się dublować

Jeśli w pliku jest frontmatter:

```md
---
title: Inwentaryzacja hostingów
---
```

oraz dodatkowo w treści:

```md
# Inwentaryzacja hostingów
```

na stronie może pojawić się podwójny tytuł. Jeśli Quartz już pokazuje tytuł z frontmatteru, to często można usunąć ręczny nagłówek `# H1`.

## `index.md` działa jak strona folderu

Jeśli folder ma swój `index.md`, Quartz traktuje go jak stronę wejściową tego katalogu.

Przykład:

```text
moje-hostingi/
├── index.md
├── domeny-i-dns/
│   └── index.md
├── hosting-debscy/
│   └── index.md
└── inwentaryzacja/
    └── index.md
```

Dzięki temu folder może być jednocześnie kategorią i normalną stroną z treścią.

## Po zmianie struktury sprawdzić 3 rzeczy

Po zmianie nazw plików, folderów albo linków warto sprawdzić:

- czy linki nadal prowadzą do właściwych notatek,
- czy na localhost nie ma pustej albo uciętej treści,
- czy Explorer po lewej pokazuje dobrą strukturę.

To pozwala szybko wychwycić problem, zanim zmiany trafią na GitHuba.

## Dobra kolejność pracy

Najbezpieczniejszy schemat pracy:

1. Edycja notatek w VS Code.
2. Sprawdzenie na localhost.
3. Poprawki, jeśli coś źle renderuje.
4. `git status`
5. `git add .`
6. `git commit -m "..."`
7. `git push`

Dzięki temu najpierw potwierdzasz, że Quartz renderuje poprawnie, a dopiero potem publikujesz.

## Krótka checklista

Przed pushem warto sprawdzić:

- [ ] Czy localhost pokazuje aktualną treść?
- [ ] Czy wikilinki działają?
- [ ] Czy nie ma linków zapisanych w backtickach?
- [ ] Czy tytuł nie dubluje się z H1?
- [ ] Czy po zmianach struktury nie trzeba zrestartować Quartza?

## Praktyczna zasada

Jeśli „w VS Code wygląda dobrze”, ale „na localhost coś się nie zgadza”, to najpierw sprawdzam:

1. czy link nie jest w backtickach,
2. czy nie użyłem dziwnej ścieżki,
3. czy nie zdublowałem tytułu,
4. czy Quartz nie wymaga restartu.
