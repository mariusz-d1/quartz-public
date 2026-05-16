---
title: Porządki i migracje
---

# Porządki i migracje

To jest nota robocza dotycząca porządkowania hostingów, DNS, stron, poczty i ewentualnych migracji.

## Zasada

Najpierw inwentaryzacja, potem analiza zależności, potem decyzje, a dopiero na końcu zmiany.

## Cele

- uprościć układ hostingów,
- ograniczyć zbędne usługi,
- ustalić, co jest aktywne,
- zmniejszyć ryzyko przypadkowego wyłączenia czegoś ważnego,
- przygotować docelowy porządek.

## Zadania

- [ ] zakończyć inwentaryzację obu hostingów
- [ ] spisać domeny, DNS, WWW, pocztę i SSL
- [ ] oznaczyć rzeczy zbędne
- [ ] oznaczyć rzeczy krytyczne
- [ ] ustalić docelowy układ usług
- [ ] rozpisać kolejność zmian

## Potencjalne ryzyka

- wyłączenie działającej poczty,
- usunięcie rekordu DNS używanego przez stronę,
- utrata przekierowania,
- wyłączenie starej, ale nadal potrzebnej usługi.

## Decyzje

- 

## Kolejność działań

1. Inwentaryzacja.
2. Oznaczenie zależności.
3. Plan docelowy.
4. Backup.
5. Zmiany techniczne.
6. Weryfikacja po zmianach.