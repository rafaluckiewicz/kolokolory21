[README.txt](https://github.com/user-attachments/files/34444288/README.txt)
# Koło Fortuny – instrukcja uruchomienia

To jest gotowa strona dla 5 osób. Każdy otwiera ten sam link, wpisuje imię i losuje jeden z kolorów: czarny, czerwony, pomarańczowy, zielony, biały. Przydział jest zapisywany atomowo w Firebase Realtime Database, więc kolory nie powinny się powtarzać, a lista aktualizuje się na żywo.

## Ważne
Nie mogę opublikować strony na Twoim koncie za Ciebie. Potrzebujesz bezpłatnego konta Google/Firebase i hostingu statycznego. Nie udostępniaj nikomu danych logowania.

## 1. Utwórz bazę Firebase
1. Wejdź na https://console.firebase.google.com/ i zaloguj się.
2. Utwórz projekt (np. `kolorowe-kolo`).
3. W projekcie wybierz **Build → Realtime Database → Create Database**.
4. Wybierz lokalizację i rozpocznij w trybie zablokowanym.
5. W **Build → Authentication → Sign-in method** włącz **Anonymous**.
6. W **Project settings → General → Your apps** dodaj aplikację Web (ikona `</>`), skopiuj konfigurację Firebase.

## 2. Ustaw reguły bazy
W Realtime Database → Rules wklej poniższe reguły i opublikuj:

```json
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
```

Te proste reguły pozwalają anonimowo zalogowanym osobom korzystać z bazy. Link należy wysłać tylko zaproszonym osobom. Nie przechowuj tu prywatnych danych. Po imprezie możesz usunąć projekt lub bazę.

## 3. Wstaw konfigurację
Otwórz `index.html` w edytorze tekstu i znajdź `const firebaseConfig = {...}`.
Zastąp wartości `WKLEJ_...` konfiguracją ze swojego projektu Firebase. `databaseURL` skopiuj dokładnie z ustawień Realtime Database.

## 4. Opublikuj stronę za darmo
Najprościej użyć GitHub Pages:
1. Załóż konto na https://github.com/
2. Utwórz publiczne repozytorium, np. `kolorowe-kolo`.
3. Dodaj do repozytorium plik `index.html`.
4. Otwórz **Settings → Pages**, wybierz **Deploy from a branch**, branch `main`, folder `/root`, zapisz.
5. Po chwili GitHub pokaże adres strony.

## 5. Wyślij wspólny link
Do adresu strony dopisz na końcu fragment:
`#zAsmeqDtvNZ2r2qV1o6lSiwF`

Przykład: `https://TWOJ-LOGIN.github.io/kolorowe-kolo/#zAsmeqDtvNZ2r2qV1o6lSiwF`

Wyślij dokładnie ten sam link wszystkim pięciu osobom. Fragment po `#` jest identyfikatorem prywatnego pokoju losowania — nie publikuj go publicznie.

## Zasady
- Maksymalnie 5 różnych imion (duplikaty imion są blokowane).
- Każdy kolor może zostać przydzielony tylko raz.
- Po rozdaniu pięciu kolorów losowanie się kończy.
- Wyniki są wspólne i aktualizują się na bieżąco.
- Ta wersja nie ma przycisku resetowania, żeby przypadkowo nie skasować wyników.
