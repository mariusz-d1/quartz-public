# Tagi w DokuWiki na regulus.net.pl

## Cel

Po uporządkowaniu namespace'ów i sidebarów kolejnym etapem było zaplanowanie systemu tagów dla przepisów w DokuWiki. Celem tagów jest dodanie drugiej warstwy porządkowania treści obok namespace'ów, tak aby przepisy można było filtrować nie tylko po dziale (`kulinaria:zupy`, `kulinaria:wypieki`), ale także po cechach takich jak rodzaj dania, dieta, czas przygotowania czy okazja. [1][2]

## Jakie pluginy tagowe były dostępne

W instalacji dostępne były dwa różne pluginy:

- **Tagging Plugin** (`plugin:tagging`) — plugin pozwalający użytkownikom oznaczać strony tagami, wyszukiwać tagi i budować chmury tagów. Jest bardziej „społecznościowy” i opiera się na adnotacjach użytkowników. [3]
- **Tag Plugin** (`plugin:tag`) — prostszy i bardziej klasyczny plugin do tagowania stron wiki. Pozwala przypisać stronie zestaw tagów i generować listy stron oznaczonych danym tagiem. [1]

Po porównaniu tych dwóch rozwiązań uznano, że dla tej wiki lepszym wyborem będzie **Tag Plugin**, ponieważ wiki ma charakter prywatnej/domowej bazy przepisów, a nie wieloużytkownikowego systemu wspólnych adnotacji. W takim zastosowaniu wygodniejsze są stałe tagi przypisane bezpośrednio do stron. [1][3]

## Dlaczego wybrano Tag Plugin

Tag Plugin lepiej pasuje do wiki z przepisami, ponieważ:

- pozwala przypisać każdej stronie prosty, jednoznaczny zestaw tagów, [1]
- daje prostą składnię osadzaną bezpośrednio w tekście strony, [1]
- dobrze nadaje się do budowy indeksów typu „wszystkie zupy”, „wszystkie szybkie przepisy”, „wszystkie wypieki słodkie”, [1][4]
- jest często używany jako podstawowy system tagowania treści w DokuWiki i ma szerokie wsparcie w dokumentacji oraz przykładach. [1][5]

## Podstawowa składnia Tag Plugin

Do oznaczenia strony tagami używana jest składnia:

```txt
{{tag>tag1 tag2 tag3}}
```

Przykłady:

```txt
{{tag>zupa wegetarianskie szybkie}}
{{tag>jednogarnkowe obiad_codzienny}}
{{tag>wypiek_chleb wolne_gotowanie}}
```

Tagi najlepiej umieszczać na końcu strony przepisu, pod treścią i ewentualnymi uwagami. [1][4]

Plugin pozwala też tworzyć strony zbierające przepisy według tagu, np. przez makra typu `{{topic>...}}`, które mogą generować listy albo tabele stron oznaczonych danym tagiem. [1][6]

## Proponowany schemat tagów

Dla tej wiki zaproponowano prosty system tagów oparty na trzech grupach.

### 1. Typ dania

- `zupa`
- `jednogarnkowe`
- `pieczen`
- `wypiek_slodki`
- `wypiek_chleb`
- `przetwor`
- `dodatek`

### 2. Dieta / ograniczenia

- `wegetarianskie`
- `weganskie`
- `bezglutenowe`
- `bez_nabialu`
- `bez_cukru`

### 3. Czas / okazja

- `szybkie`
- `wolne_gotowanie`
- `obiad_codzienny`
- `swieta`
- `impreza`

Założenie było takie, aby nie tworzyć od razu setek tagów, tylko zacząć od małego, przewidywalnego słownika i rozszerzać go dopiero wtedy, gdy pojawi się realna potrzeba. Tagi miały być drugą warstwą organizacji obok namespace'ów, a nie ich zamiennikiem. [1][2]

## Przykłady tagowania stron

Przykładowe przypisania tagów do istniejących przepisów:

- `kurczak_tikka_masala` → `{{tag>jednogarnkowe obiad_codzienny}}`
- `zupa_czosnkowa` → `{{tag>zupa wegetarianskie szybkie}}`
- `chleb_na_zakwasie` → `{{tag>wypiek_chleb wolne_gotowanie}}`

Takie podejście pozwala później przeglądać przepisy nie tylko według miejsca w drzewie wiki, ale również według wspólnych cech. [1][4]

## Propozycja strony zbiorczej `kulinaria:tagi`

Zaproponowano utworzenie strony `kulinaria:tagi`, która miałaby działać jako przegląd tagów i indeks przepisów po tagach. Przykładowa zawartość:

```txt
====== Przepisy wg tagów ======

===== Typ dania =====

  * {{topic>zupa&table&header&tags&nodesc&firsthl}}
  * {{topic>jednogarnkowe&table&header&tags&nodesc&firsthl}}
  * {{topic>wypiek_chleb&table&header&tags&nodesc&firsthl}}
  * {{topic>wypiek_slodki&table&header&tags&nodesc&firsthl}}
  * {{topic>przetwor&table&header&tags&nodesc&firsthl}}

===== Dieta =====

  * {{topic>wegetarianskie&table&header&tags&nodesc&firsthl}}
  * {{topic>weganskie&table&header&tags&nodesc&firsthl}}
  * {{topic>bezglutenowe&table&header&tags&nodesc&firsthl}}

===== Czas / okazja =====

  * {{topic>szybkie&table&header&tags&nodesc&firsthl}}
  * {{topic>wolne_gotowanie&table&header&tags&nodesc&firsthl}}
  * {{topic>obiad_codzienny&table&header&tags&nodesc&firsthl}}
```

Na początek zalecono jednak podejście minimalistyczne: najpierw dodać tagi do kilku istniejących przepisów, utworzyć prostą stronę `kulinaria:tagi`, a dopiero potem rozbudowywać listy i tabele. [1][6]

## Link do strony tagów ze strony startowej

Aby udostępnić użytkownikowi łatwy dostęp do strony tagów, zaproponowano dodanie linku do strony `kulinaria:tagi` na stronie głównej `start`. Składnia linku wewnętrznego DokuWiki ma postać:

```txt
[[kulinaria:tagi|Przepisy wg tagów]]
```

Przykład osadzenia w stronie `start`:

```txt
===== Dodatkowo =====

Zobacz też [[kulinaria:tagi|Przepisy wg tagów]].
```

Taki link wykorzystuje standardową składnię linków wewnętrznych DokuWiki, w której przed pionową kreską znajduje się pełne ID strony, a po niej tekst widoczny dla użytkownika. [7]

## Wnioski

Na obecnym etapie nie wdrożono jeszcze pełnego systemu tagowania wszystkich stron, ale ustalono kierunek i podstawy techniczne:

- wybrano **Tag Plugin** jako główny mechanizm tagów, [1]
- odrzucono Tagging Plugin jako mniej potrzebny w prywatnej wiki przepisowej, [3]
- ustalono początkowy słownik tagów, [1]
- zaplanowano stronę zbiorczą `kulinaria:tagi`, [1][6]
- przygotowano składnię linku do tej strony ze strony głównej. [7]

Kolejny praktyczny krok to dodać tagi do kilku wybranych przepisów testowych i sprawdzić, jak wygląda strona `kulinaria:tagi` po pierwszym zasileniu rzeczywistymi danymi.