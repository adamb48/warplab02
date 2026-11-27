# HelloWorkshop

## Kontakt
autor: Adam B
zespół warsztat programisty

## Uruchomienie z komendą
dotnet run

## Continuous Integration

Projekt korzysta z GitHub Actions. Konfiguracja znajduje się w pliku `.github/workflows/build.yml`.

### Kiedy uruchamia się workflow

- po pushu do brancha `main`,
- dla Pull Requesta skierowanego do `main` (także po kolejnych pushach do brancha tego PR),
- ręcznie, przyciskiem **Run workflow** (`workflow_dispatch`).

### Sprawdzany projekt

- Projekt: `HelloWorkshop` (`./HelloWorkshop.csproj`)
- Wersja .NET SDK: `10.0.x`

### Automatyczne kontrole

1. **Struktura repozytorium:** skrypt `scripts/check-repository.sh` sprawdza, czy podano ścieżkę do projektu, czy plik projektu istnieje oraz czy `README.md` istnieje i nie jest pusty.
2. **Restore:** pobranie zależności projektu.
3. **Build:** kompilacja w konfiguracji `Release`.
4. **Publish:** przygotowanie opublikowanej wersji aplikacji w katalogu `./artifacts/app`.
5. **Run:** uruchomienie zbudowanej aplikacji.

Jeśli któryś krok zakończy się błędem, kolejne kroki są domyślnie pomijane, a workflow kończy się niepowodzeniem.

### Artefakt

Wynik jest zapisywany jako artefakt `app-<sha>`, gdzie `<sha>` to id commita, dla którego działa workflow. Artefakt jest przechowywany przez 7 dni.

### Logi i artefakty

1. Otwórz zakładkę **Actions** w repozytorium na GitHubie.
2. Wybierz workflow **Build .NET project**, a następnie konkretne uruchomienie.
3. Aby zobaczyć logi, otwórz job **build** i rozwiń wybrany krok.
4. Aby pobrać artefakt, na stronie podsumowania uruchomienia przejdź do sekcji **Artifacts**.