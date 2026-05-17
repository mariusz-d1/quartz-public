---
title: DokuWiki na regulus.net.pl — porządkowanie
---

# DokuWiki na regulus.net.pl — porządkowanie wiki

## Cel

Wiki pod adresem `https://dokuwiki.regulus.net.pl/` ma być domową bazą wiedzy:
- przepisy kulinarne,
- wypieki i słodkości,
- przetwory,
- domowe środki czystości.

Celem prac była zmiana starego szablonu na nowy, ogarnięcie sidebara i wstępne uporządkowanie struktury namespace'ów.

---

## Stan początkowy

- Aktywny template: **roundbox** (stary, ciężki wizualnie, mało czytelny).
- Strona `start` zawierała:
  - powitanie,
  - pełne „drzewko” wiki,
  - nawigację mocno wymieszaną z treścią.
- Sidebar:
  - istniały strony typu `czyszczenie_domu:sidebar` z `{{indexmenu>}}`,
  - brak jasnego podziału na globalny sidebar i lokalne sidebary,
  - użycie `{{indexmenu>:}}` w niektórych miejscach (za szeroki zakres).

Efekt: trudno było odróżnić, co jest treścią strony, a co właściwym panelem bocznym.

---

## Backup

Przed zmianami wykonano **pełny backup katalogu `dokuwiki`** z poziomu panelu hostingu:

- w `public_html` spakowano do ZIP cały folder `dokuwiki`,
- archiwum ma w nazwie datę (łatwe rozpoznanie),
- backup zawiera:
  - treść wiki (`data/pages`, `data/media`, `data/meta`, `data/attic`),
  - konfigurację (`conf`),
  - pluginy i szablony (`lib/plugins`, `lib/tpl`).

Na razie ZIP leży na hostingu; pobranie lokalnie zostanie zrobione później, po ogarnięciu hasła do FTP/WinSCP.

---

## Zmiana template na sprintdoc

### Aktualizacja i aktywacja

- Template **sprintdoc** był już zainstalowany, ale nieaktywny.
- W konfiguracji:
  - jako `template` ustawiono `sprintdoc`,
  - w polu `sidebar` pozostawiono `sidebar` (globalna strona sidebara).
- Sprawdzono ustawienia motywu sprintdoc:
  - `sidebar_sections = All headings` — nagłówki w `sidebar` tworzą sekcje,
  - `autocollapse` zaznaczone,
  - `closedwiki` **wyłączone** (wiki nie jest zamknięta przed zalogowaniem),
  - `header_layout = header-default`.

Po tych zmianach sidebar zaczął działać jako lewy panel (z sekcjami typu „Nawigacja”, „Kuchnia”, „Dom”, „Szybki dostęp”), a strona główna przestała być „zielonym monolitem” jak przy roundboxie.

---

## Uporządkowanie strony startowej

Strona `start` została wyczyszczona z nawigacji i drzewek.

Aktualna treść:

```txt
====== Strona startowa ======

Witaj w mojej wiki.

To miejsce na:
  * przepisy kulinarne
  * wypieki
  * przetwory
  * domowe środki czystości

Skorzystaj z menu po lewej stronie, aby przejść do odpowiedniego działu.
```

Dzięki temu:
- sidebar jest jedynym miejscem nawigacji,
- strona startowa jest krótka i czytelna,
- układ sprintdoc (lewy panel + treść) działa tak, jak zaprojektowano.

---

## Sidebar — obecny stan

### Globalny `:sidebar`

- Ustalono, że **globalny `sidebar`** ma być prostym ręcznym menu głównych działów, bez pełnego drzewa wszystkich stron.
- Treść została uproszczona do linków typu:
  - `[[start|Strona główna]]`,
  - `[[kulinaria:kulinaria|Kulinaria]]`,
  - `[[kulinaria:wypieki:wypieki|Wypieki]]`,
  - `[[kulinaria:wypieki:slodkosci:slodkosci|Słodkości]]`,
  - `[[kulinaria:zupy:zupy|Zupy]]`,
  - `[[kulinaria:szynkowar:szynkowar|Szynkowar]]`,
  - `[[czyszczenie_domu:start|Domowe środki]]`.

Sprintdoc rozbija nagłówki na sekcje i pokazuje je w eleganckich ramkach w lewym panelu — wizualnie jest OK.

### Lokalne sidebary

Potwierdzono, że DokuWiki używa **„najbliższej strony `sidebar`”** dla danego namespace:

- `czyszczenie_domu:sidebar` — lokalny sidebar działu sprzątanie,
- `kulinaria:sidebar` — lokalna nawigacja kulinarna,
- opcjonalnie `kulinaria:wypieki:sidebar` — jeszcze bardziej zawężony panel dla wypieków.

W lokalnych sidebarach:

- zastąpiono zbyt szerokie `{{indexmenu>:}}` wywołaniami:
  - `{{indexmenu>czyszczenie_domu#1|navbar notoc}}`,
  - `{{indexmenu>kulinaria#1|navbar notoc}}`,
  - `{{indexmenu>kulinaria:wypieki#1|navbar notoc}}`,
- usunięto opcję `js` z indexmenu, aby pozbyć się ostrzeżenia o konflikcie z `defer_js`.

Efekt: indexmenu generuje drzewko tylko dla danego działu, a nie dla całej wiki, i nie ma ostrzegawczych komunikatów.

---

## Rozpoznanie struktury namespace'ów

Na podstawie indeksu wiki ustalono aktualną strukturę:

Główne namespace’y:

- `czyszczenie_domu`
- `kulinaria`
- `playground`
- `wiki`
- root (bez prefiksu) — kilka pojedynczych stron kulinarnych

Wewnątrz `kulinaria`:

- `kulinaria:jednogarnkowce`
- `kulinaria:pieczone`
- `kulinaria:szynkowar`
- `kulinaria:wypieki`
  - `kulinaria:wypieki:pieczywo`
  - `kulinaria:wypieki:slodkosci`
- `kulinaria:zupy`

W root (bez namespace) nadal wisiało kilka „osieroconych” stron kulinarnych, które logicznie należą do powyższych działów.

---

## Przenoszenie stron — Move Plugin

Zamiast ręcznie grzebać w plikach `data/pages`, zdecydowano się użyć **Move Plugin**:

- plugin dodaje akcję „Rename/Move page”,
- przenoszenie strony = nadanie jej nowego ID z namespace,
- przykładowe przeniesienie:

  - było: `kurczak_tikka_masala`
  - jest: `kulinaria:jednogarnkowce:kurczak_tikka_masala`

Mechanika:
- wpisuje się pełne ID docelowe, np. `kulinaria:jednogarnkowce:kurczak_tikka_masala`,
- plugin przenosi stronę do odpowiedniego namespace, zachowując historię
  i (w zależności od konfiguracji) poprawiając linki i media.

---

## Plan przenosin (pierwsza paczka)

Ustalono wstępny plan przeniesienia „osieroconych” stron z root namespace do logicznych działów.

### Do `kulinaria:jednogarnkowce`

- `garam_masala` → `kulinaria:jednogarnkowce:garam_masala`
- `majuddara` → `kulinaria:jednogarnkowce:majuddara`
- `peczak_po_meksykansku` → `kulinaria:jednogarnkowce:peczak_po_meksykansku`
- `potrawka_z_czerwona_soczewica_i_cukinia` → `kulinaria:jednogarnkowce:potrawka_z_czerwona_soczewica_i_cukinia`
- `potrawka_z_soczewicy_z_cukinia` → `kulinaria:jednogarnkowce:potrawka_z_soczewicy_z_cukinia`
- `makaron_w_sosie_serowo_szpinakowym` → `kulinaria:jednogarnkowce:makaron_w_sosie_serowo_szpinakowym`
- `makaron_z_sosem_serowym` → `kulinaria:jednogarnkowce:makaron_z_sosem_serowym`
- `makaron_poledwiczka_wieprzowa_sosie_serowo_szpinakowym_queijo_curado` → `kulinaria:jednogarnkowce:makaron_poledwiczka_wieprzowa_sosie_serowo_szpinakowym_queijo_curado`
- `tortille_ze_szpinakiem_i_serem` → `kulinaria:jednogarnkowce:tortille_ze_szpinakiem_i_serem`
- `zapiekanka_warzywna` → `kulinaria:jednogarnkowce:zapiekanka_warzywna`

### Do `kulinaria:pieczone`

- `pieczen_bieszczadzka` → `kulinaria:pieczone:pieczen_bieszczadzka`
- `zeberka_pieczone` → `kulinaria:pieczone:zeberka_pieczone`
- `zeberka_w_miodzie` → `kulinaria:pieczone:zeberka_w_miodzie`
- `kurczak_na_ryzu_pieczarkami` → `kulinaria:pieczone:kurczak_na_ryzu_pieczarkami`
- `kurczak_sosie_smietanowym` → `kulinaria:pieczone:kurczak_sosie_smietanowym`
- `gulasz_z_zoladkow_drobiowych` → `kulinaria:pieczone:gulasz_z_zoladkow_drobiowych`
- `zoladki_gesie` → `kulinaria:pieczone:zoladki_gesie`
- `klops` → `kulinaria:pieczone:klops`

*(opcjonalnie można kiedyś wydzielić osobny namespace `kulinaria:podroby:*`)*

### Do `kulinaria:zupy`

- `zupa_czosnkowa` → `kulinaria:zupy:zupa_czosnkowa`

### Do `kulinaria:wypieki:slodkosci`

- `placek_z_masa_makowa` → `kulinaria:wypieki:slodkosci:placek_z_masa_makowa`

### Do `kulinaria:przetwory_domowe`

- `przyprawa_meksykanska` → `kulinaria:przetwory_domowe:przyprawa_meksykanska`
- `lemoniada_miodowa` → `kulinaria:przetwory_domowe:lemoniada_miodowa`
- `salatka_z_burakow_kiszonych` → `kulinaria:przetwory_domowe:salatka_z_burakow_kiszonych`
- `salatka_z_porow` → `kulinaria:przetwory_domowe:salatka_z_porow`

---

## Stan po obecnym etapie

- wiki działa na template **sprintdoc**,
- sidebar jest czytelny i faktycznie siedzi po lewej,
- strona `start` jest uporządkowana,
- potwierdzono działanie globalnego i lokalnych sidebarów,
- indexmenu działa bez opcji `js` i bez konfliktu z `defer_js`,
- pierwsze przepisy (np. `kurczak_tikka_masala`) zostały już przeniesione do właściwych namespace’ów.

Kolejny etap to sukcesywne przenoszenie reszty stron z root do odpowiednich namespace’ów oraz dalsze dopieszczanie sidebara w działach (np. lepsze „szybkie dostępy” i linki do ulubionych przepisów).

Pierwszy test przeniesienia wykonano na stronie `kurczak_tikka_masala`, która została skutecznie przeniesiona z root namespace do `kulinaria:jednogarnkowce:kurczak_tikka_masala`. Potwierdziło to, że mechanizm Rename/Move działa poprawnie na tej instalacji.