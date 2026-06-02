# Toidutellimused

### Toidutellimused on veebirakendus, mis võimaldab kasutajatel esitada ja hallata toidutellimusi. Rakendus pakub funktsionaalsust tellimuste loomise, vaatamise, muutmise ja kustutamise jaoks ning võimaldab jälgida tellimuste staatust. Süsteem on mõeldud nii klientidele kui ka administraatoritele tellimuste efektiivseks haldamiseks.

## Tehnoloogiad

- Node.js
- Express.js
- PostgreSQL
- Docker
- Jest
- GitHub Actions

## Keskkondade erinevused

| | Dev | Prod |
|--|-----|------|
| Port | 3000 | 3001 |
| Logid | Detailne arenduslogi konsoolis | Ainult olulised info- ja vealogid |
| Restart | Nodemon (automaatne restart koodi muutmisel) | PM2 või Docker (automaatne taaskäivitus serveris) |

## Käivitamine

### Dev keskkond

Paigalda sõltuvused:

```bash
npm install
```

### Prod keskkond

#### Tootmiskeskkond on mõeldud lõppkasutajatele. Rakenduse kasutamiseks tuleb avada veebileht või mobiilirakendus. Eraldi käivitamine kasutaja poolt ei ole vajalik.
``` bash
www.toidutellimused.ee
```
## Testid

Testide käivitamiseks kasuta järgmist käsku:

```bash
npm test
```

## API

Rakendus kasutab REST API-t toidutellimuste haldamiseks.

### Tellimused

#### GET /api/orders
Tagastab kõik tellimused.

#### GET /api/orders/:id
Tagastab konkreetse tellimuse ID järgi.

#### POST /api/orders
Loob uue tellimuse.

#### PUT /api/orders/:id
Uuendab olemasolevat tellimust.

#### DELETE /api/orders/:id
Kustutab tellimuse.

### Vastuse formaat (näide)

```json
{
  "id": 1,
  "customerName": "Mari Maasikas",
  "items": [
    {
      "productId": 2,
      "quantity": 1
    }
  ],
  "status": "pending"
}

```

## GitHub Actions

GitHub Actions automatiseerib arendusprotsessi ja tagab koodi kvaliteedi.

Iga kord kui tehakse push või pull request peaharusse, käivitatakse automaatselt:

- sõltuvuste installimine
- testide käivitamine
- koodi kvaliteedikontroll (lintimine)
- rakenduse buildimine

Kui mõni samm ebaõnnestub, märgitakse workflow ebaõnnestunuks ning muudatusi ei lubata peaharusse liita enne vea parandamist.
