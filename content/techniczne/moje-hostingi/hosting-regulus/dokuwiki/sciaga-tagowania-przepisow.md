# Tagowanie przepisów – ściąga

Konwencja:

- małe litery,
- bez polskich znaków,
- spacje zamieniane na `_`,
- tagi wpisywane na końcu strony w jednym wierszu, np. `{{tag>przepis obiad jednogarnkowe kuchnia_polska na_szybko}}`. Składnia pochodzi z pluginu Tag dla DokuWiki. [1]

## Rodzaj strony

Te tagi warto stosować konsekwentnie, żeby odróżniać przepisy od zwykłych notatek:

- `przepis`
- `notatka_kuchnia`
- `notatka_dom`

## Typ dania

Najczęściej wystarczy wybrać 1–2 tagi z tej listy:

- `obiad`
- `zupa`
- `sniadanie`
- `kolacja`
- `przekaska`
- `deser`
- `wypieki_slodkie`
- `wypieki_wytrawne`
- `dodatki`
- `napoj`

## Sposób przygotowania / sprzęt

- `jednogarnkowe`
- `pieczenie`
- `patelnia`
- `garnki`
- `szynkowar`
- `wolnowar`
- `grill`
- `bez_pieczenia`
- `na_zimno`

## Kuchnia / region

- `kuchnia_polska`
- `kuchnia_wloska`
- `kuchnia_indyjska`
- `kuchnia_azjatycka`
- `kuchnia_meksykanska`
- `kuchnia_srodziemnomorska`

## Cechy dania

- `wegetarianskie`
- `weganskie`
- `bez_glutenu`
- `bez_laktozy`
- `low_carb`
- `na_szybko`
- `tani`
- `dla_dzieci`
- `na_impreze`
- `do_pudelka`

## Sezon / okazja

- `sezon_wiosna`
- `sezon_lato`
- `sezon_jesien`
- `sezon_zima`
- `swieta`
- `wielkanoc`
- `grill_party`

## Gotowe przykłady

### Ciasto z jabłkami

```text
{{tag>przepis obiad deser wypieki_slodkie pieczenie kuchnia_polska sezon_jesien tani}}
```

### Zupa dahl z czerwonej soczewicy

```text
{{tag>przepis obiad zupa kuchnia_indyjska wegetarianskie weganskie jednogarnkowe na_szybko tani}}
```

### Szynkowa z szynkowara

```text
{{tag>przepis obiad wypieki_wytrawne szynkowar kuchnia_polska do_pudelka tani}}
```

## Minimalny zestaw na start

Żeby nie przesadzić z liczb теп tagów, na początku warto trzymać się prostego schematu:

- zawsze: `przepis`,
- 1–2 tagi typu dania,
- 0–2 tagi sposobu przygotowania / sprzętu,
- 0–1 tag kuchni,
- 0–2 tagi cech.

W praktyce daje to zwykle 4–7 tagów na stronę, co jest dobrym kompromisem między porządkiem a wygodą późniejszego wyszukiwania. [1]