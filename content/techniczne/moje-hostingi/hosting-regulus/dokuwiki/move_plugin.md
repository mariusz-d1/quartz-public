## Jak przenosić stronę Move Pluginem

Najwygodniej przenosić pojedyncze strony przez funkcję **Rename/Move page**.

### Procedura

1. Otworzyć stronę, którą trzeba przenieść, np. `kurczak_tikka_masala`.
2. Kliknąć akcję **Rename page** / **Move page**.
3. W polu nowej nazwy wpisać **pełne nowe ID strony**, razem z namespace, np.:

   ```txt
   kulinaria:jednogarnkowce:kurczak_tikka_masala
   ```

4. Zatwierdzić zmianę.
5. Sprawdzić, czy strona otwiera się pod nowym adresem.
6. Sprawdzić, czy pojawia się poprawnie w indeksie oraz w lokalnym sidebarze / `indexmenu`.

### Zasada

W DokuWiki przeniesienie strony do namespace oznacza po prostu nadanie jej nowego pełnego ID:

- wszystko przed ostatnim `:` = namespace,
- ostatni człon = nazwa strony.

Przykład:

- `kulinaria:jednogarnkowce` = namespace
- `kurczak_tikka_masala` = nazwa strony

### Przykład

Było:

```txt
kurczak_tikka_masala
```

Po przeniesieniu jest:

```txt
kulinaria:jednogarnkowce:kurczak_tikka_masala
```

### Dobra praktyka

Najlepiej przenosić strony:
- po jednej albo małymi paczkami po 3–5,
- po każdej paczce sprawdzić indeks wiki,
- upewnić się, że sidebar i `indexmenu` pokazują już nowe położenie strony.

### Uwagi

- Nie przenosić stron ręcznie przez menedżer plików hostingu, jeśli nie ma takiej konieczności.
- Move Plugin jest bezpieczniejszy, bo pracuje na poziomie logiki DokuWiki.
- Po większej serii przenosin warto sprawdzić, czy nie zostały stare linki w stronach zbiorczych i sidebarach.