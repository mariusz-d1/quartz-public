## Przenoszenie lokalnych sidebarów do namespace'ów

Po uporządkowaniu struktury namespace'ów i aktywowaniu szablonu **sprintdoc** okazało się, że lokalne sidebary dla działu kulinarnego były zapisane jako zwykłe strony w root namespace:

- `kulinaria_sidebar` → plik `data/pages/kulinaria_sidebar.txt`
- `kulinaria_wypieki_sidebar` → plik `data/pages/kulinaria_wypieki_sidebar.txt`

To działało, ale było sprzeczne z zalecanym wzorcem DokuWiki, w którym lokalny sidebar dla namespace'u powinien nazywać się po prostu `sidebar` i leżeć _w tym namespace_, np.:

- `:sidebar` → globalny sidebar (root)
- `kulinaria:sidebar` → sidebar dla `kulinaria:*`
- `kulinaria:wypieki:sidebar` → sidebar dla `kulinaria:wypieki:*`

### 1. Przeniesienie `kulinaria_sidebar` → `kulinaria:sidebar`

Strona `kulinaria_sidebar` zawierała dopracowane menu dla całych kulinariów:

```txt
====== Kulinaria ======

  * [[start|Strona główna]]
  * [[kulinaria:kulinaria|Strona działu Kulinaria]]

====== Działy ======

  * [[kulinaria:jednogarnkowce:jednogarnkowce|Jednogarnkowce]]
  * [[kulinaria:pieczone|Pieczone]]
  * [[kulinaria:wypieki:wypieki|Wypieki]]
  * [[kulinaria:wypieki:slodkosci:slodkosci|Słodkości]]
  * [[kulinaria:zupy:zupy|Zupy]]
  * [[kulinaria:szynkowar|Szynkowar]]

====== W tym dziale ======

{{indexmenu>kulinaria#1|navbar notoc}}
```

Zamiast kombinować w menedżerze plików, strona została **przeniesiona przez Rename/Move**:

- stare ID: `kulinaria_sidebar`
- nowe ID: `kulinaria:sidebar`

Efekt końcowy na poziomie plików:

```txt
data/pages/kulinaria/sidebar.txt
```

Dzięki temu:

- globalny sidebar to nadal `:sidebar` (root),
- dla stron `kulinaria:*` wykorzystywany jest lokalny `kulinaria:sidebar`,
- DokuWiki stosuje zasadę „najbliższy sidebar wygrywa” – lokalne menu kulinarne nadpisuje globalne.

### 2. Przeniesienie `kulinaria_wypieki_sidebar` → `kulinaria:wypieki:sidebar`

Analogicznie rozwiązano lokalny sidebar dla wypieków. Strona `kulinaria_wypieki_sidebar` (w root) miała treść:

```txt
====== Wypieki ======

  * [[start|Strona główna]]
  * [[kulinaria:kulinaria|Kulinaria]]
  * [[kulinaria:wypieki:wypieki|Strona działu Wypieki]]

====== Poddziały ======

  * [[kulinaria:wypieki:pieczywo:chleb_na_zakwasie|Pieczywo — przykład]]
  * [[kulinaria:wypieki:slodkosci:slodkosci|Słodkości]]

====== W tym dziale ======

{{indexmenu>kulinaria:wypieki#1|navbar notoc}}
```

Została przeniesiona Rename/Move do:

- stare ID: `kulinaria_wypieki_sidebar`
- nowe ID: `kulinaria:wypieki:sidebar`

Co dało plik:

```txt
data/pages/kulinaria/wypieki/sidebar.txt
```

Po tym kroku:

- `kulinaria:sidebar` jest lokalnym menu dla całych kulinariów,
- `kulinaria:wypieki:sidebar` jest jeszcze bardziej szczegółowym menu dla wypieków i ma pierwszeństwo dla stron `kulinaria:wypieki:*`,
- root namespace przestał zawierać techniczne „*_sidebar” – zostały tylko `start`, `sidebar` i katalogi namespace'ów.

### 3. Dlaczego tak jest lepiej

- struktura plików odpowiada dokładnie logice namespace'ów,
- każdy dział może mieć swoje własne menu, bez mieszania wszystkiego w globalnym `:sidebar`,
- łatwiej będzie w przyszłości dodać kolejne sidebary (np. `czyszczenie_domu:sidebar`) w dokładnie taki sam sposób.

Na tym etapie wiki ma:
- globalny sidebar dla całej instalacji,
- dedykowany sidebar dla `kulinaria:*`,
- dedykowany sidebar dla `kulinaria:wypieki:*`,
- czysty root bez roboczych stron sidebarowych.