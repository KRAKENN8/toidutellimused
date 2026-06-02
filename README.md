# Toidutellimused

Toidutellimused on veebirakendus toidu tellimiseks interneti kaudu. Rakendus võimaldab kasutajatel registreeruda, sisse logida, sirvida menüüd ning filtreerida roogasid erinevate kategooriate järgi, et leida sobivaid tooteid ja esitada tellimusi mugavalt veebikeskkonnas.

## Tehnoloogiad

* JavaScript – rakenduse loogika ja funktsionaalsus
* HTML – veebilehtede struktuur
* CSS – kasutajaliidese kujundus
* Docker – rakenduse käivitamine

## Keskkondade erinevused

| | Dev | Prod |
|--|-----|------|
| Port | 3000 | 3001 |
| Logid | Logid salvestatakse Dockeri kaudu | Logid salvestatakse Dockeri kaudu |
| Restart | Taaskäivitatakse kuni käsitsi peatamiseni | Taaskäivitatakse alati automaatselt |

## Käivitamine

### Dev keskkond

Käivitab rakenduse arenduskeskkonnas kasutades Nodemonit, mis taaskäivitab serveri automaatselt failide muutmisel: nodemon src/server.js

### Prod keskkond

Käivitab rakenduse tootmiskeskkonnas kasutades Node.js-i ilma automaatse taaskäivitamiseta: node src/server.js

## Testid

Testide käivitamiseks käivita käsk: node src/test.js

## API

### Health check

Serveri staatuse kontrollimiseks kasutatakse endpointi **GET /health**, mis tagastab info selle kohta, kas rakendus töötab korrektselt.

### Kasutajad

Kasutajate haldamiseks on olemas kaks endpointi.
Uue kasutaja registreerimiseks kasutatakse **POST /api/users/signup**, mille kaudu luuakse uus kasutajakonto.
Sisselogimiseks kasutatakse **POST /api/users/login**, mis võimaldab kasutajal autentida end süsteemi.

### Menüü

Toidumenüü andmete vaatamiseks kasutatakse endpointi **GET /api/menu**, mis tagastab kogu saadaval oleva menüü info.

### Tellimused

Tellimuse loomiseks kasutatakse endpointi **POST /api/orders**, mille kaudu saab kasutaja esitada uue tellimuse.


## GitHub Actions

Kui projektis oleks seadistatud GitHub Actions CI töövoog, siis iga kord kui kood pushitakse GitHubi repositooriumisse, käivituks automaatne protsess, mis seab üles Node.js keskkonna, installib sõltuvused ning käivitab testid, et kontrollida API korrektset toimimist enne muudatuste liitmist põhiharusse.
