
---
title: Publikacja lokalna
draft: false
---
> [!note]
> Lokalny podgląd przez `npx quartz build --serve` nie wykonuje commita, nie wysyła plików na GitHuba i nie publikuje strony. Jest bezpieczny do testów.

> [!warning]
> Jeżeli dana notatka ma w nagłówku YAML:
>
> ```yaml
> draft: true
> ```
>
> Quartz ukryje ją i adres wpisu może zwrócić błąd `404`.
>
> Aby zobaczyć wpis w lokalnym podglądzie, ustaw:
>
> ```yaml
> draft: false
> ```
>
> Nie wykonuj commita i pusha z `draft: false`, dopóki wpis nie jest gotowy do publicznej publikacji.