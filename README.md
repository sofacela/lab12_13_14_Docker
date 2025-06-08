Laby 12, 13, 14 – LEMP + Docker Compose

Zestaw trzech laboratoriów w jednym repozytorium:

Lab 12 – Podstawowy LEMP + phpMyAdmin
 - [`lab12_docker/`](./lab12_docker)

- Prosty stack LEMP
- Konfiguracja w jednym `docker-compose.yml`

Lab 13 – Docker Secrets
 - [`lab13_docker/`](./lab13_docker)

- Przekazywanie danych przez Docker secrets
- `*_FILE` i folder `secrets/` (wykluczony z repozytorium)

Lab 14 – Podział Compose (base + override)
 - [`lab14_docker/`](./lab14_docker)

- `docker-compose.yml` + `docker-compose.override.yml`
- Modularna konfiguracja

---

Uruchamianie

W każdej podfolderze (`lab12_docker`, `lab13_docker`, `lab14_docker`) znajduje się lokalny `README.md` z instrukcjami.

---

Bezpieczeństwo

Foldery `secrets/` w lab13 i lab14 są **wykluczone z repozytorium** (`.gitignore`), dzięki czemu dane uwierzytelniające nie są publikowane.

---

Komentarz techniczny

Repozytorium pokazuje ewolucję projektu Docker:
- Od prostej konfiguracji (Lab 12)
- Przez poprawę bezpieczeństwa (Lab 13)
- Do dobrej praktyki modularnej (Lab 14)