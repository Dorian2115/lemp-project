**Uzasadnienie sieci dla phpMyAdmin:** phpMyAdmin jest podłączony do obu sieci
(backend i frontend), ponieważ jeżeli byłby podłączony tylko do jednej z nich,
to:

- **backend** — phpMyAdmin musi komunikować się z MySQL, który jest tylko w
  sieci backend. Bez tego nie mógłby się połączyć z bazą
- **frontend** — bez dostępu do sieci frontend phpMyAdmin nie byłby dostępny z
  zewnątrz, czyli przez port na maszynie hosta

### Polecenia lab13

#### Uruchomienie

```bash
docker compose up -d
```

#### Weryfikacja statusu kontenerów

```bash
docker compose ps
```

#### Potwierdzenie działania aplikacji

#### Zatrzymanie i usunięcie

```bash
docker compose down
docker compose down -v
```

### Polecenia lab13D

#### Usunięcie starego wolumenu MySQL

```bash
docker volume rm lemp-project_mysql_data
```

#### Uruchomienie z secrets

```bash
docker compose -f docker-compose.secrets.yml up -d
```

#### Weryfikacja montowania sekretów

```bash
docker inspect lemp-mysql
```

![Screenshot](https://github.com/Dorian2115/lemp-project/blob/main/zrzutyEkranu/Zrzut%20ekranu_20260612_135423.png)

MySQL przy pierwszym uruchomieniu inicjalizuje bazę i ustawia hasła. Przy
kolejnym uruchomieniu ignoruje zmienne środowiskowe i sekrety, dlatego usuwamy
wolumen przed uruchomieniem docker-compose.secrests.yml (w plikach secrets były
podane inne hasła niż w wersji docker-compose.yml).
