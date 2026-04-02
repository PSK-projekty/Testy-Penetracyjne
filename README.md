# Pentest Vuln App

`Pentest Vuln App` to celowo podatna aplikacja webowa napisana we Flasku w ramch projetu Testy Penetracyjne.

## O projekcie

Aplikacja udostępnia klasyczny zestaw funkcji webowych:

- rejestrację, logowanie i wylogowanie,
- profil użytkownika,
- wyszukiwarkę,
- upload plików,
- narzędzie `ping`,
- czytnik plików,
- panel administracyjny.

W projekcie znajdują się również gotowe materiały pomocnicze do demonstracji podatności w katalogu `pentest-app/docs/poc/` oraz opisy poszczególnych podatności w `pentest-app/docs/vulnerabilities/`.

## Jak startuje aplikacja

Po uruchomieniu aplikacji wykonywana jest funkcja `create_app()` z pakietu `pentest-app/app/`.

Oznacza to, że aplikacja:

- ładuje zmienne środowiskowe z pliku `.env`,
- tworzy wymagane katalogi dla bazy, sesji i uploadów,
- inicjalizuje sesje Flask-Session,
- podłącza SQLite jako bazę danych,
- przy pierwszym starcie inicjalizuje schemat bazy i zakłada domyślne konto administratora.

Domyślne dane administratora:

- login: `admin`
- hasło: `Admin123!`

Aplikacja domyślnie startuje na porcie `5000` i jest wystawiana pod adresem `http://127.0.0.1:5000`.

## Wymagania

- Python `3.12` lub nowszy,
- `pip`,
- opcjonalnie `venv`,
- opcjonalnie Docker i Docker Compose.

Zależności runtime są opisane w `requirements.txt` w katalogu głównym. Jeśli chcesz uruchomić także testy, użyj pliku `pentest-app/requirements.txt`.

## Uruchomienie lokalne

1. Przejdź do katalogu głównego repozytorium.
2. Utwórz i aktywuj środowisko wirtualne.
3. Zainstaluj zależności.
4. Uruchom aplikację.

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python pentest-app/run.py
```

Po starcie aplikacja będzie dostępna pod `http://127.0.0.1:5000`.

## Testy

Projekt ma zestaw testów automatycznych opartych o `pytest` i `pytest-cov`.

Aktualny stan pokrycia testami:

- `54` testy,
- około `99%` pokrycia kodu,
- testy obejmują backend, frontend i scenariusze podatności.

Uruchomienie testów:

```powershell
pip install -r pentest-app/requirements.txt
pytest --cov=pentest-app --cov-report=term-missing
```

## Podatności

| ID | Nazwa podatności | Realizujący |
| --- | --- | --- |
| VULN-01 | Session Fixation | Marek Supierz |
| VULN-02 | Reflected XSS | do uzupełnienia |
| VULN-03 | CSRF | do uzupełnienia |
| VULN-04 | Insecure File Upload | do uzupełnienia |
| VULN-05 | Command Injection | do uzupełnienia |
| VULN-06 | Security Misconfiguration | do uzupełnienia |
| VULN-07 | Path Traversal | Andrzej Mysior |

Szczegółowe opisy, payloady i PoC znajdują się w:

- `pentest-app/docs/vulnerabilities/`
- `pentest-app/docs/poc/`

