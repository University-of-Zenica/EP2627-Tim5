# Tehnološke smjernice

Službena dokumentacija provjerena: **16. 11. 2026.**

## Izbor alata

Opis zadatka predlaže dbt Core ili SQLMesh za SQL modele te Apache Superset
za izvještaje. U fazi inicijalizacije izbor alata za transformacije ostaje otvoren.
Tim treba odabrati jedan alat i bazu prije dodavanja izvršne konfiguracije.

SQLMesh podržava transformacije u SQL-u i Pythonu, testove i provjere podataka.
Upute za odabir i postavljanje dostupne su u
[službenoj dokumentaciji SQLMesh-a](https://sqlmesh.readthedocs.io/en/stable/).

Apache Superset je open-source platforma za istraživanje i vizualizaciju
podataka koja se povezuje na SQL baze. Služit će za prikaz rezultata modela.
Izvor: [Apache Superset](https://superset.apache.org/).

## Napomena o dbt-u u 2026. godini

Službena dokumentacija razlikuje dbt v2 (serija 2.x) i Python generaciju
dbt v1 (serija 1.x). Na datum provjere v1.12 ima aktivnu podršku, a v1.13
je beta. Za zahtjev za Apache 2.0 runtimeom dokumentacija upućuje na dbt OSS.
Zato prije instalacije treba provjeriti konkretnu distribuciju, podršku za
odabranu bazu i kompatibilnost adaptera, umjesto prepisivanja starih uputa.
Izvor: [About dbt versions](https://docs.getdbt.com/docs/dbt-versions).

## Pravilo verzioniranja okruženja

- Pri postavljanju odabrati najnovija stabilna, međusobno kompatibilna izdanja.
- Provjeriti podržanu verziju Pythona za svaki alat i adapter; sama dostupnost
  najnovijeg Pythona ne znači da ga svi alati podržavaju.
- Zabilježiti točne verzije ovisnosti u konfiguraciji i pripadajućoj lock datoteci.
- Ako se koriste kontejneri, navesti točan tag verzije ili digest slike.
- Nadogradnje provoditi kroz zaseban pull request uz provjeru modela i dashboarda.

Ovaj početni commit nema instalacijske ovisnosti, slike kontejnera ni pokrenute
servise. Provjera dokumentacije nije provjera izvršavanja ili kompatibilnosti
budućeg okruženja. To će se provjeriti pri njegovom postavljanju.
