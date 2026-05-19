# ACL i uprawnienia w DokuWiki na regulus.net.pl

## Dlaczego w ogóle ACL

Po uporządkowaniu struktury wiki i zmianie szablonu okazało się, że na innym komputerze można wejść w edycję stron **bez logowania**.  
To nie był „bug”, tylko domyślne zachowanie DokuWiki – świeża instalacja pozwala każdemu edytować i tworzyć strony, dopóki nie włączysz i nie ustawisz kontroli dostępu (ACL).

Celem było:

- zablokowanie edycji dla anonimowych użytkowników,
- pozostawienie publicznego **odczytu** wiki,
- pełna edycja tylko po zalogowaniu.

## Jak działa ACL w DokuWiki (w skrócie)

DokuWiki ma wbudowany mechanizm **Access Control List (ACL)**.  
Uprawnienia przyznaje się:

- dla całego wiki (root `:`),
- dla namespace’ów (np. `kulinaria:*`, `czyszczenie_domu:*`),
- dla pojedynczych stron,
- dla użytkowników i grup.

Kluczowe wbudowane grupy:

- `@ALL` – wszyscy (zalogowani i niezalogowani),
- `@user` – wszyscy zalogowani użytkownicy,
- `@admin` – administratorzy.

Poziomy uprawnień (rosnące):

- `none` – brak dostępu,
- `read` – czytanie,
- `edit` – edycja istniejących stron,
- `create` – tworzenie nowych stron,
- `upload` – upload plików,
- `delete` – usuwanie,
- `admin` – pełne administrowanie (dla superuserów).

W praktyce – im wyższy poziom, tym zawiera w sobie niższe (np. `upload` zawiera też `read`, `edit`, `create`).

## Docelowy model uprawnień dla tej wiki

Założenia dla domowej bazy przepisów:

- anonimowi:
  - mogą **czytać** całą wiki,
  - nie mogą edytować, tworzyć, usuwać, uploadować;
- zalogowani (właściciel / rodzina):
  - mogą czytać wszystko,
  - mogą edytować / tworzyć przepisy,
  - mogą uploadować zdjęcia do przepisów.

Przekłada się to na:

- `@ALL` – `read` na całym wiki,
- `@user` – `edit/create/upload` w przestrzeniach z treścią domową (`kulinaria:*`, `czyszczenie_domu:*`),
- `@user` – ewentualnie tylko `read` w `wiki:*` (dokumentacja systemowa).

## Konfiguracja krok po kroku

W GUI DokuWiki:

1. Zalogować się jako **admin**.
2. Wejść w **Admin** (link w nagłówku).
3. Wybrać **Access Control List Management** (Zarządzanie listą kontroli dostępu / ACL).
4. W drzewku z lewej wybrać **root** (`:`), żeby ustawić regułę domyślną.
5. W tabeli reguł:
   - znaleźć **grupę `@ALL`** i ustawić jej uprawnienia na **Read** (tylko odczyt),
   - dodać / sprawdzić wpis dla **`@user`** – nadać mu co najmniej **Edit** (a jeśli potrzeba, też Create/Upload).
6. Zatwierdzić zmiany przyciskiem **Update/Save**.

Po tej operacji:

- użytkownik niezalogowany nie powinien widzieć przycisku „Edytuj” (albo po kliknięciu dostanie komunikat o braku uprawnień),
- zalogowany użytkownik (Ty) zachowuje możliwość pełnej edycji.

## Przykładowa logika reguł (do odtworzenia)

Na poziomie root (`:`):

- `@ALL` – `Read`
- `@user` – `Edit` (lub wyżej)

Na poziomie `kulinaria:*`:

- `@ALL` – `Read`
- `@user` – `Edit/Create/Upload`

Na poziomie `czyszczenie_domu:*`:

- `@ALL` – `Read`
- `@user` – `Edit/Create/Upload`

Na poziomie `wiki:*` (opcjonalnie):

- `@ALL` – `Read`
- `@user` – `Read`

To daje prosty model: **wszyscy czytają, edytują tylko zalogowani**.

## Jak sprawdzić, że działa

Test z drugiego laptopa / innej przeglądarki:

1. Wejść na wiki **bez logowania**.
2. Sprawdzić, czy przycisk „Edytuj”:
   - nie jest widoczny, albo
   - po kliknięciu wymaga logowania.
3. Spróbować przejść do `start`, jakiejś strony kulinarnej i do `wiki:syntax`, żeby zobaczyć, że wszystkie są do odczytu, ale nie do edycji.

Jeśli gdzieś nadal można edytować bez logowania, trzeba wrócić do ACL i sprawdzić, czy dla tego namespace’u nie zostało przypadkiem ustawione coś wyższego niż `Read` dla `@ALL`.

---

W razie potrzeby można tę notatkę rozszerzyć o szczegółowy zrzut z aktualnych reguł ACL (np. wypisując je w stylu `* @ALL 1`, `kulinaria:* @user 8`), ale na razie taki opis logiczny powinien wystarczyć jako ściągawka.