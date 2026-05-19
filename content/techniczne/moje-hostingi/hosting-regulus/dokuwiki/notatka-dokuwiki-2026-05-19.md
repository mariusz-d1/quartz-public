# Notatka z 2026-05-19 — porządki w DokuWiki

Dzisiejsza praca skupiła się na uporządkowaniu prywatnej wiki tak, żeby z luźnego brudnopisu zrobić sensowną, publicznie pokazywalną bazę wiedzy o kuchni, przepisach i domu. Zmieniono tytuł wiki na „Domowa wiki: kuchnia i przepisy”, przygotowano nową stronę startową, dopracowano docelową strukturę namespace'ów, zaktualizowano szablon przepisu i ustalono workflow dla zdjęć oraz porządków w starych działach. [file:631][web:512][web:637]

## Kierunek organizacji wiki

Zamiast mieszać różne porządki w jednym drzewie, przyjęto prostszy podział na cztery główne działy: `przepisy:`, `kuchnia:`, `spizarnia:` i `dom:`. W DokuWiki namespace'y działają jak foldery i tworzą się automatycznie, gdy zakłada się strony z nazwami rozdzielonymi dwukropkami. [web:512][web:640]

Przyjęta zasada porządkowania jest taka, że namespace'y służą do stabilnych, szerokich działów, a tagi do cech przepisu. Oznacza to, że rzeczy takie jak `jednogarnkowe`, `pieczone`, `wegetarianskie` czy `kuchnia_indyjska` powinny działać głównie jako tagi, a nie jako osobne główne foldery. [web:512][web:637]

## Docelowa struktura

Docelowy układ ma wyglądać następująco:

- `przepisy:` — gotowe dania, zupy, wypieki, desery, dodatki, śniadania i napoje.
- `kuchnia:` — techniki, sprzęt, bazy i notatki warsztatowe, np. szynkowar, zakwas, buliony.
- `spizarnia:` — przetwory, kiszonki i zapasy.
- `dom:` — czyszczenie, organizacja i inne praktyczne notatki domowe.
- `wiki:` — rzeczy techniczne i systemowe.
- `playground:` — testy i brudnopis. [web:512][web:637]

Na podstawie istniejącej zawartości ustalono przykładowe mapowanie starych działów do nowych. `czyszczenie_domu:` ma trafić do `dom:`, `kulinaria:zupy:*` do `przepisy:zupy:*`, `kulinaria:przetwory_domowe:*` do `spizarnia:przetwory:*`, a różne rzeczy związane z szynkowarem do `kuchnia:techniki:szynkowar:*`. [file:631]

## Strona startowa i sidebary

Przygotowano nową treść strony `start`, która działa jako prosty portal wejściowy do głównych działów wiki. To jest zgodne z dobrą praktyką DokuWiki, według której strona startowa powinna opisywać cel wiki i prowadzić do najważniejszych namespace'ów. [web:637][web:512]

Ustalono też, że sidebary można robić per namespace przez zwykłe strony o nazwie `sidebar`. DokuWiki korzysta z najbliższej strony `sidebar`, więc można mieć zarówno globalne `:sidebar`, jak i osobne `przepisy:sidebar`, `kuchnia:sidebar`, `spizarnia:sidebar` i `dom:sidebar`. [web:637]

## Szablon przepisu

Podmieniono automatyczny szablon namespace'owy na nowszą wersję. DokuWiki obsługuje takie szablony przez pliki `_template.txt` i `__template.txt`, przy czym `__template.txt` działa również w podnamespace'ach. [web:507][web:514]

Nowa wersja szablonu przepisu została rozbudowana o sekcje `Źródło / oryginał`, `Moje wykonanie i modyfikacje` oraz `Uwagi po przygotowaniu`. To rozwiązuje problem większości przepisów pochodzących z zewnętrznych źródeł, bo pozwala na jednej stronie trzymać zarówno przepis bazowy, jak i własne poprawki, bez mnożenia osobnych stron dla każdej wariacji. [web:507][web:655]

## Zdjęcia i workflow graficzny

Ustalono, że zdjęcia do wiki najlepiej trzymać w uporządkowanej strukturze odpowiadającej stronom, np. w media namespace'ach odpowiadających przepisom. DokuWiki obsługuje obrazy przez standardową składnię `{{...}}`, można też od razu ustawiać miniatury i podpisy. [web:491][web:637]

Dla zdjęć z telefonu przyjęto praktyczny standard przygotowania przed uploadem: JPG, dłuższy bok około 1600 px, jakość około 80%, najlepiej obrabiane hurtowo w XnView MP. Takie pliki są dużo lżejsze od oryginałów 8–10 MB, a nadal w zupełności wystarczają do treści wiki i wydruków PDF. [web:690]

W zakresie archiwizacji zdjęć ustalono roboczy workflow: aparat dalej działa przez kartę pamięci i import do digiKam według sesji dziennych, natomiast telefon najlepiej traktować jako źródło plików kopiowanych przez USB do folderu „intake”, a dopiero później porządkowanych w digiKam. MTP i bezpośredni import telefonu do digiKam bywają mniej przewidywalne, więc lepiej oprzeć się na prostym kopiowaniu plików i późniejszym porządkowaniu kolekcji. [web:690]

## Usuwanie starych stron i namespace'ów

Wyjaśniono, że w tej instalacji Sprintdoc nie pokazuje osobnego przycisku „Usuń” w interfejsie strony. Nie jest to problem, bo DokuWiki domyślnie usuwa stronę wtedy, gdy zapisze się ją jako pustą. [web:500][web:690][web:707]

Przyjęto więc prostą metodę porządków: najpierw przenieść treść do nowego miejsca, potem — jeśli potrzeba — zostawić chwilowo notkę „strona została przeniesiona do...”, a ostatecznie wejść w edycję starej strony, wyczyścić jej zawartość do zera i zapisać. Gdy znikną wszystkie strony z danego starego namespace'u, sam namespace również zniknie z indeksu. [web:500][web:690]

## Wniosek roboczy

Najważniejsze ustalenie z dzisiejszej pracy jest takie, że wiki przestaje być tylko prywatnym, publicznie wystawionym brudnopisem, a zaczyna przypominać spójną domową bazę wiedzy. Fundament pod to już jest: nowa nazwa, lepsza strona startowa, sensowna struktura działów, lepszy szablon przepisu i prosty sposób porządkowania starych stron bez walki z interfejsem. [file:631][web:512][web:500]
