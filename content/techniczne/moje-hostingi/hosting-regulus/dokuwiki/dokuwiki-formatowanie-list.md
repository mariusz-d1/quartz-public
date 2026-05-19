# Formatowanie list, bloków i szablonu przepisu w DokuWiki

## Problem z blokiem "kodowym" przy przepisach

Podczas formatowania opisu przygotowania potrawy (np. chlebki pita) pojawił się problem: cały fragment "Przygotowanie" wyświetlał się w ciemniejszej ramce z poziomym przewijaniem, jak blok kodu, zamiast jako zwykły tekst lub lista kroków.

Przyczyną był sposób wcięcia i łamania linii — DokuWiki potraktowało wcięty tekst jako **blok preformatowany (code block)**, ponieważ linie zaczynały się od spacji. [1][2]

## Zasada: wcięcia = blok preformatowany

W DokuWiki:

- jeśli linia zaczyna się od co najmniej dwóch spacji, jest interpretowana jako **blok preformatowany**, podobnie jak wstawka kodu,
- taki blok jest renderowany w ramce, ze stałą szerokością i często z poziomowym scrollowaniem,
- jest to mechanizm przeznaczony dla fragmentów kodu, logów itp., nie dla treści przepisu. [1][2]

Przykład problematycznego zapisu (wszystkie linie wcięte):

```txt
Przygotowanie:

    Wsyp drożdże do miseczki...
    W dużej misce wymieszaj mąkę z solą...
    Ugniataj ciasto...
```

Taki zapis powoduje, że cały blok po nagłówku "Przygotowanie" traktowany jest jako tekst preformatowany.

## Poprawny zapis listy kroków

Aby DokuWiki potraktowało fragment jako listę, a nie blok kodu, trzeba:

1. **Dać pustą linię po nagłówku**.
2. Zacząć każdy punkt od `-` lub `*` (lub numeru), **bez wiodących spacji**.
3. Upewnić się, że **każdy punkt jest w osobnej fizycznej linii** (czyli po każdym kroku Enter).

Przykład poprawnego formatu:

```txt
===== Przygotowanie =====

- Wsyp drożdże do miseczki, dodaj cukier, zalej 5 łyżkami letniej wody i wszystko wymieszaj, aż drożdże się rozpuszczą. Odstaw na ok. 15 minut. W gotowym zaczynie pojawią się bąbelki dwutlenku węgla (tzn. że nasze drożdże ożyły).

- W dużej misce wymieszaj mąkę z solą. Dolej zaczyn i oliwę. Wymieszaj, ja to robię łyżką. Stopniowo dolewaj letnią wodę, po troszeczku (1-2 łyżki), bo łatwo przesadzić. Dolej porcję wody, wymieszaj łyżką lub rękoma, po czym dodaj kolejną porcję, jeżeli ciasto jest nadal za suche. Gdy zauważysz, że zaczęło łączyć się w większe grudy, zacznij je ugniatać ręką. Wyczujesz wtedy, czy dodać jeszcze trochę wody, czy nie.

- Ugniataj ciasto, aż stanie się gładkie i elastyczne. Zajmuje to niestety ok. 8-10 minut i trochę trzeba się pomęczyć. Aby sprawdzić, czy ciasto jest gotowe, trzeba je nacisnąć palcem - wgniecenie powinno samo zniknąć.

- Wyrobione ciasto włóż do miski wysmarowanej oliwą, przykryj czystą ściereczką i odstaw do wyrośnięta na 1-1,5 godziny. Powinno podwoić swoją objętość. Teraz należy ciasto odgazować uderzając w nie kilkakrotnie pięścią.

- Podziel ciasto na 8 części i z każdej uformuj kulkę. Ułóż je na desce lekko posypanej mąką, przykryj ściereczką i odstaw do wyrośnięcia na 25 minut. W tym czasie włóż blachę do pieczenia do piekarnika i nagrzej go do 230 stopni.

- Kulki ciasta rozwałkuj cienko na grubość 3-4 mm. Wyjmij blachę z piekarnika, szybko ułóż na niej placki i wstaw z powrotem do piekarnika. Piecz przez 3-5 minut, aż placki napęcznieją.

===== Uwagi =====
```

Kluczowe elementy:

- nagłówek zapisany jako `===== Przygotowanie =====` (nagłówek poziomu 5),
- **pusta linia** po nagłówku przed pierwszym elementem listy,
- każdy element listy w osobnej linii, zaczynający się od `-` bez dodatkowych spacji z przodu,
- opcjonalnie pusta linia między elementami listy dla czytelności.

W takim układzie DokuWiki tworzy klasyczną listę, bez ramki i poziomego scrolla. [1][3]

## Szybka checklista przy edycji przepisów

Przy każdej sekcji typu "Przygotowanie" warto sprawdzić:

- Czy nagłówek jest zapisany jako `===== Przygotowanie =====`, a nie "Przygotowanie:" w zwykłym tekście.
- Czy po nagłówku jest pusta linia.
- Czy kroki zaczynają się od `-` lub `1.` bez wcięć.
- Czy po każdym kroku jest Enter (każdy krok w osobnej linii).
- Czy nie ma niepotrzebnych spacji na początku linii (bo zmienią blok w preformatowany).

Jeśli nagle cały blok ląduje w ramce jak kod albo pojawia się poziomy scroll, pierwsze co trzeba sprawdzić to właśnie **wiodące spacje** i brak pustych linii przed listą.

## Prosty szablon przepisu

Żeby nie walczyć później z formatowaniem za każdym razem od nowa, warto używać prostego, powtarzalnego układu strony przepisu.

Przykładowy szablon:

```txt
====== Nazwa przepisu ======

Krótki opis przepisu.

===== Składniki =====

- 500 g mąki
- 7 g suchych drożdży
- 1 łyżeczka soli
- 1 łyżeczka cukru
- 2 łyżki oliwy
- letnia woda

===== Przygotowanie =====

- Krok 1...
- Krok 2...
- Krok 3...

===== Uwagi =====

- Można przygotować dzień wcześniej.
- Najlepiej podawać na ciepło.

{{tag>wypiek_chleb wolne_gotowanie}}
```

Taki układ daje kilka korzyści:

- wszystkie przepisy wyglądają podobnie,
- łatwiej później poprawiać styl i strukturę,
- tagi są zawsze w tym samym miejscu,
- sekcje są czytelne zarówno w treści strony, jak i w nawigacji / spisie treści.

## Zalecenie praktyczne

Najlepiej podczas tworzenia nowych przepisów kopiować gotowy szablon i podmieniać tylko treść. Dzięki temu unika się najczęstszych błędów:

- przypadkowego bloku kodu przez spacje,
- braku pustej linii po nagłówku,
- zlania kroków przygotowania w jeden akapit,
- pominięcia tagów na dole strony.