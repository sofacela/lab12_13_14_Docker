Lab 12 – LEMP stack + phpMyAdmin (Docker Compose)

Co zostało zrealizowane

Projekt zawiera:
- Kontener `nginx`, który obsługuje `index.php` i działa na porcie `4001`
- Kontener `php-fpm`, który interpretuje kod PHP
- Kontener `mysql:5.7` z użytkownikiem, hasłem i przykładową bazą danych
- Kontener `phpmyadmin`, dostępny na porcie `6001`, połączony z MySQL

Użyte zostały obrazy z tagami z DockerHub, połączone odpowiednimi sieciami `backend` i `frontend`.

Struktura projektu

```
lab12_docker/
├── docker-compose.yml
├── README.md
├── php/
│   └── index.php
├── nginx/
│   └── default.conf
├── screenshots/
    └── (zrzuty ekranu potwierdzające działanie)
```

Jak uruchomić

1. Otwórz terminal w katalogu projektu
2. Uruchom komendę:

```bash
docker compose up --build
```

Jeśli chcesz uruchomić kontenery w tle (detached):

```bash
docker compose up -d
```

Jak zatrzymać

Aby zatrzymać kontenery:

```bash
docker compose down
```

Aby wyjść z trybu logów bez zatrzymywania kontenerów (gdy uruchomiono bez `-d`):

```bash
Ctrl + P, potem Ctrl + Q
```

Jak sprawdzić

- `http://localhost:4001` — powinien wyświetlić stronę `phpinfo()`
- `http://localhost:6001` — panel phpMyAdmin
  - Login: `root`
  - Hasło: `root`

Dlaczego phpMyAdmin jest w dwóch sieciach?

Kontener `phpmyadmin` został dołączony do:
- `frontend`, aby był widoczny z zewnątrz (localhost:6001)
- `backend`, aby mógł komunikować się z serwerem `mysql`, który również znajduje się w tej sieci.

Dzięki temu zachowana jest separacja warstw aplikacji i bezpieczeństwo – tylko potrzebne usługi mają do siebie dostęp.

Wyniki działania

Zrzuty ekranu, które pokazują polecenia wraz z wynikiem ich działania znajdują się w katalogu: `screenshots/`

Weryfikacja

- Działa strona startowa `index.php`
- Można zalogować się do phpMyAdmin
- Można utworzyć testową bazę danych
