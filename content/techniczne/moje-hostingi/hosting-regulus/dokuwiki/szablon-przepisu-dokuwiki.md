# Szablon notatki przepisu kulinarnego do DokuWiki

Poniżej gotowy szablon do wklejania przy tworzeniu nowej strony z przepisem. Używa podstawowej składni DokuWiki: nagłówków, list i prostych tabel. [1][2][3]

## Wersja do wklejenia

```text
====== @!PAGE@ ======

===== Opis =====
Krótki opis przepisu: co to jest, na ile osób i w jakiej sytuacji najlepiej się sprawdza.

===== Informacje podstawowe =====
^ Pole ^ Wartość ^
| Kategoria | obiad / zupa / deser / pieczywo / sałatka |
| Kuchnia | polska / włoska / indyjska / inna |
| Czas przygotowania |  |
| Czas gotowania / pieczenia |  |
| Łączny czas |  |
| Porcje |  |
| Poziom trudności | łatwy / średni / trudniejszy |
| Sprzęt | piekarnik / blender / garnek / patelnia |

===== Składniki =====
==== Główne ====
  * 
  * 
  * 

==== Przyprawy / dodatki ====
  * 
  * 
  * 

===== Przygotowanie =====
  - 
  - 
  - 
  - 
  - 

===== Wskazówki =====
  * Na co uważać:
  * Co można przygotować wcześniej:
  * Jak przechowywać:
  * Jak odgrzewać:

===== Zamienniki =====
  * Składnik → zamiennik
  * Składnik → zamiennik

===== Podanie =====
  * Z czym podawać:
  * Dodatki:
  * Dekoracja:

===== Notatki własne =====
  * Co wyszło dobrze:
  * Co poprawić następnym razem:
  * Wersja testowa / data:

===== Źródło =====
  * Link:
  * Autor / inspiracja:

{{tag>przepis}}
```

## Uwagi praktyczne

DokuWiki obsługuje nagłówki przez znaki `=` oraz listy punktowane `*` i numerowane `-`, więc ten układ powinien wkleić się bez problemu do zwykłego edytora strony. [1][2] Prosta tabela na początku dobrze nadaje się do czasu, porcji i poziomu trudności, ale list wewnątrz tabeli lepiej unikać bez dodatkowych pluginów. [4][5]

Jeżeli chcesz, taki szablon można później zamienić na automatyczny `_template.txt` dla namespace z przepisami, żeby DokuWiki samo go wstawiało przy tworzeniu nowej strony. DokuWiki wspiera też znaczniki zastępcze w szablonach stron, np. `@PAGE@`, `@DATE@` czy `@USER@`. [6]