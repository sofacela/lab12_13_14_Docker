Lab 14 – LEMP stack + Docker Secrets + Compose Override

Co zostało zrealizowane

Projekt został zmodyfikowany względem Lab 13:

- Plik `docker-compose.yml` został rozdzielony na:
  - `docker-compose.yml` – (bazowy) podstawowa konfiguracja aplikacji
  - `docker-compose.override.yml` – konfiguracja środowiska deweloperskiego (ports, volumes, secrets)
- Wszystkie dane wrażliwe nadal są przekazywane przez mechanizm Docker secrets.
- Została zachowana poprawna struktura sieci (frontend + backend)

Struktura projektu

```
lab14_lemp_override/
├── docker-compose.yml
├── docker-compose.override.yml
├── php/
│   └── index.php
├── nginx/
│   └── default.conf
├── secrets/
│   ├── mysql_root_password
│   ├── mysql_user
│   ├── mysql_password
│   └── mysql_database
└── screenshots/
    └── ... (zrzuty ekranu)
```

Jak uruchomić

```bash
docker compose up --build
```

Docker automatycznie połączy `.yml` bazowy + `override.yml`.

Jak zatrzymać

```bash
docker compose down
```

Wyjście z logów bez zatrzymywania:

```bash
Ctrl + P, potem Ctrl + Q
```

Jak sprawdzić

- `http://localhost:4001` → phpinfo()
- `http://localhost:6001` → phpMyAdmin (login: `root`, hasło: `root`)

Weryfikacja (screenshots/)

- Widoczność strony `phpinfo()`
- Logowanie do phpMyAdmin
- Baza `testdb` utworzona automatycznie

Różnica względem Lab 13

Zastosowano mechanizm **override Compose** (podział pliku na środowiska)