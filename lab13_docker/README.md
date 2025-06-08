Lab 13 – LEMP stack + Docker Secrets (Docker Compose)

Co zostało zrealizowane

Projekt został zmodyfikowany względem Lab 12:

- Zmieniono sposób przekazywania danych uwierzytelniających do kontenera `mysql`
- Zastosowano mechanizm `Docker secrets`:
  - dane uwierzytelniające nie są zapisane jawnie w `docker-compose.yml`
  - wykorzystywane są pliki `*_FILE` w `/run/secrets/...`
- Sekcja `secrets:` została dodana zarówno na poziomie usług, jak i globalnie

Struktura projektu

```
lab13_restore/
├── docker-compose.yml
├── php/
│   └── index.php
├── nginx/
│   └── default.conf
├── secrets/
│   ├── mysql_root_password
│   ├── mysql_user
│   ├── mysql_password
│   └── mysql_database
├── screenshots/
    └── ... (zrzuty ekranu)
```

Jak uruchomić

```bash
docker compose up --build
```

Aby uruchomić kontenery w tle (detached):

```bash
docker compose up -d
```

Jak zatrzymać

```bash
docker compose down
```

Aby wyjść z logów:

```bash
Ctrl + P, potem Ctrl + Q
```

Jak sprawdzić

- `http://localhost:4001` → phpinfo()
- `http://localhost:6001` → phpMyAdmin
  - Login: `root`
  - Hasło: `root` (czytane z sekreta)

Weryfikacja

- Widoczność strony `phpinfo()`
- Logowanie do phpMyAdmin
- Baza danych `testdb` utworzona automatycznie

Różnice względem Lab 12:

- Zamiast `MYSQL_ROOT_PASSWORD`, `MYSQL_DATABASE` itd.
- Użyto `*_FILE` i przekazano dane jako Docker secrets
- Lepsze bezpieczeństwo i separacja konfiguracji