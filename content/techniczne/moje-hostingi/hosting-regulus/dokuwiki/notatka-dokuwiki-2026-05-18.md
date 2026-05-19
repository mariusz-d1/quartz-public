# Notatka z 2026-05-18 — DokuWiki / Sprintdoc

Dzisiaj dopracowano dwa poboczne, ale praktyczne elementy prywatnej wiki kulinarnej: faviconę oraz możliwość wygodnego wydruku przepisu do PDF z kodem QR prowadzącym do aktualnej wersji online. Szablon Sprintdoc obsługuje favicony przez pliki wrzucone do przestrzeni `wiki:` i nie wymaga osobnego panelu ustawień dla tej funkcji. [1][2]

## Favicon w Sprintdoc

W Sprintdoc minimalny zestaw to `wiki:logo.png` lub `wiki:logo.svg`, a faviconę można dodać przez `wiki:favicon.ico`; jako fallback szablon wspiera też `wiki:favicon.png` lub `wiki:favicon.svg`. [1] W praktyce wystarczyło wgrać do namespace `wiki:` pliki favicony, bez dodatkowego ustawiania w panelu. [2][1]

Wybrany kierunek graficzny favicony nawiązuje stylem do domyślnej ikonki DokuWiki, ale zamiast biurowego motywu wykorzystuje bardziej kulinarny znak — kartkę przepisu z zielonym akcentem. To lepiej pasuje do prywatnej wiki z przepisami, a jednocześnie zachowuje skojarzenie z DokuWiki.

## Eksport notatki do PDF

Najbardziej sensownym rozwiązaniem do wydruku pojedynczej notatki okazał się plugin `dw2pdf`, który służy do eksportu stron DokuWiki do PDF i ma ustawienia dostępne w Configuration Manager. [3][4] Dla pojedynczej strony eksport można uruchomić parametrem `do=export_pdf` dodanym do adresu otwartej notatki. [4]

Plugin pozwala też sterować eksportem przez parametry URL, m.in. ustawiając format strony, orientację, template PDF i inne opcje związane z wyglądem dokumentu. [4] Gdyby w przyszłości była potrzebna ładniejsza wersja wydruku do kuchni, wygląd PDF da się dopracować przez własny template. [5][6]

## QR w wydruku

Najprzyjemniejszym odkryciem było to, że obecny układ PDF już zawiera blok z linkiem do wiki, permalinkiem oraz kodem QR odnoszącym się do oryginalnej strony. W szablonach `dw2pdf` dostępna jest zmienna `@QRCODE@`, która wstawia obraz QR kierujący do adresu źródłowej notatki. [5][7]

To dobrze pasuje do planowanego sposobu używania wiki: na co dzień korzystanie głównie online z telefonu, tabletu i laptopa, a wydruk traktowany bardziej jako wygodna wersja dla znajomych lub kartka robocza do kuchni. Jeśli po kilku miesiącach ktoś będzie chciał sprawdzić, czy przepis się zmienił, może po prostu zeskanować kod QR z wydruku i od razu otworzyć aktualną wersję strony. [5]

## Wnioski robocze

Na teraz nie ma potrzeby dalej ruszać favicony ani wyglądu stopki PDF, bo obecne ustawienie już spełnia praktyczną funkcję. Najważniejsze jest to, że Sprintdoc poprawnie podchwytuje faviconę z `wiki:`, a `dw2pdf` daje szybki wydruk z przydatnym QR bez dodatkowych kombinacji. [2][1][3]