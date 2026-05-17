# DokuWiki na regulus.net.pl — postęp prac

## Cel

Celem było uporządkowanie wyglądu i nawigacji w DokuWiki postawionej na `dokuwiki.regulus.net.pl`, tak aby wiki mogła służyć jako baza przepisów kulinarnych, wypieków, przetworów i domowych środków czystości.

## Stan początkowy

Na początku aktywny był template `roundbox`, który działał, ale był wyraźnie przestarzały wizualnie i dawał ciężki, mało czytelny układ strony.[1]

Sidebar i zawartość strony startowej były ze sobą częściowo pomieszane, przez co drzewko stron wyświetlało się także w głównej treści strony `start`, co utrudniało ocenę właściwego układu nawigacji.[2][3]

## Decyzje techniczne

Wybrano przejście na template `sprintdoc`, ponieważ jest nowoczesny, responsywny, obsługuje standardowy mechanizm `sidebar` i był aktualizowany również w 2026 roku.[4]

Przed zmianami wykonano pełny backup całego katalogu instalacji DokuWiki, co jest zgodne z zaleceniami dokumentacji DokuWiki, według której najprościej i najbezpieczniej jest archiwizować całą instalację wiki.[5][6]

## Wykonane działania

### 1. Backup

W panelu hostingu wykonano kopię całego katalogu `dokuwiki` do archiwum ZIP z datą. Taki backup obejmuje jednocześnie treść wiki, konfigurację, pluginy i szablony, ponieważ DokuWiki przechowuje dane w plikach, a nie w klasycznej bazie SQL.[5][7]

Na ten moment kopia znajduje się na hostingu. Pobranie jej lokalnie przez FTP/WinSCP zostało odłożone do czasu rozwiązania problemu z hasłem dostępowym.

### 2. Zmiana template

Template `sprintdoc` był już wcześniej zainstalowany, ale nieaktywny. Został ustawiony jako aktywny motyw w konfiguracji DokuWiki.[4]

W konfiguracji ogólnej pozostawiono aktywne pole `sidebar = sidebar`, dzięki czemu sprintdoc korzysta ze strony `sidebar` jako lewego panelu nawigacyjnego.[3][2]

### 3. Ustawienia sprintdoc

W ustawieniach motywu pozostawiono m.in. opcję automatycznego dzielenia sidebara na sekcje na podstawie wszystkich nagłówków (`sidebar_sections = All headings`). Dokumentacja sprintdoc wskazuje, że nagłówki w stronie `sidebar` są używane do organizacji sekcji nawigacyjnych.[4]

Opcji `closedwiki` nie włączano, aby standardowe funkcje wiki, w tym sidebar, były dostępne normalnie po zalogowaniu i w zwykłym użyciu.[4]

### 4. Porządkowanie sidebara

Potwierdzono, że DokuWiki obsługuje zarówno globalną stronę `sidebar`, jak i lokalne sidebary w namespace'ach, przy czym używana jest najbliższa strona `sidebar` dla danego działu.[2][3]

W praktyce oznacza to możliwość utrzymywania:
- jednego głównego `sidebar` dla całej wiki,
- osobnych sidebarów np. dla `czyszczenie_domu`, `kulinaria` lub `kulinaria:wypieki`.[2]

W lokalnych sidebarach użyto pluginu `indexmenu`, ale bez opcji `js`, ponieważ ta opcja powoduje ostrzeżenie o konflikcie z ustawieniem `defer_js` w DokuWiki.[8][9][10]

### 5. Uporządkowanie strony startowej

Strona `start` została uproszczona. Usunięto z niej robocze drzewko stron i pozostawiono krótki tekst powitalny, tak aby główna treść nie dublowała nawigacji dostępnej w sidebarze.[2]

Dzięki temu stało się jasne, że sidebar rzeczywiście działa jako osobny panel boczny, a wcześniejsze wrażenie „sidebara w środku strony” wynikało z bałaganu w treści `start`.

## Aktualna struktura treści

Z indeksu stron wynika, że główne namespace'y wiki to przede wszystkim `czyszczenie_domu`, `kulinaria`, `playground` oraz `wiki`, a wewnątrz `kulinaria` istnieją podziały takie jak `jednogarnkowce`, `pieczone`, `szynkowar`, `wypieki` i `zupy`.[11][12]

W obrębie `kulinaria:wypieki` istnieją kolejne podnamespace'y, m.in. `pieczywo` i `slodkosci`.[12][13]

Jednocześnie część stron nadal znajduje się w root namespace, czyli poza główną strukturą działów. To one będą kandydatami do późniejszego uporządkowania i przenosin.[12][14]

## Wnioski

Najważniejsze elementy techniczne są już ogarnięte:
- wykonano backup,
- aktywowano nowy template,
- uporządkowano stronę startową,
- potwierdzono działanie globalnego i lokalnych sidebarów,
- wyeliminowano problem z `indexmenu` i opcją `js`.

Na tym etapie interfejs jest już używalny i estetyczny. Kolejny krok to zaplanowanie przenosin stron osieroconych z root namespace do właściwych działów tematycznych.