# Automatyczny szablon dla namespace `kulinaria`

DokuWiki automatycznie wczytuje zawartość pliku `_template.txt` podczas tworzenia nowej strony w danym namespace. [1][2] Jeśli użyjesz `__template.txt`, ten sam szablon zadziała także w podnamespace'ach, czyli np. `kulinaria:zupy:` albo `kulinaria:desery:`. [2][3]

## Co zrobić

1. Wejdź na serwer przez FTP lub menedżer plików hostingu. [4][5]
2. Otwórz katalog odpowiadający namespace `kulinaria`, zwykle:
   - `data/pages/kulinaria/` dla stron,
   - i właśnie tam wgraj plik `__template.txt`, jeśli chcesz objąć też podkatalogi, albo `_template.txt`, jeśli tylko sam namespace `kulinaria`. [2][5]
3. Przy tworzeniu nowej strony w `kulinaria:` DokuWiki wstawi treść szablonu automatycznie do edytora. [1][2]

## Co zawiera szablon

Szablon używa podstawowej składni DokuWiki: nagłówków, tabel i list, więc działa bez dodatkowych pluginów. [6] Dodałem też znaczniki zastępcze `@PAGE@`, `@USER@` i `@DATE@`, które DokuWiki potrafi automatycznie podmienić przy tworzeniu strony. [2][4]

## Co polecam

Dla Twojej wiki lepszy będzie plik `__template.txt`, bo wtedy jeden wzór przepisu zadziała od razu także w takich działach jak `kulinaria:jednogarnkowce:` albo `kulinaria:wypieki:`. [2][3]