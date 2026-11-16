# EP2627-Tim5 — Izvještajni model prodaje

Timski projekt za akademsku 2026/2027. godinu: izrada izvještajnog modela
s ključnim pokazateljima prodaje (KPI) korištenjem SQL-a i open-source alata.

## Cilj projekta

Pripremiti pouzdane podatke o prodaji i prikazati ih kroz interaktivne izvještaje.
Model će omogućiti praćenje prihoda, narudžbi, prodanih količina i prodajnih
trendova te analizu po proizvodu, kupcu i vremenskom periodu, ovisno o izvoru podataka.

## Trenutni status

Inicijalna struktura repozitorija (`chore: initialize project repository`).
Dodani su dokumentacija, pravila ignoriranja lokalnih datoteka i direktoriji
za budući razvoj. SQL modeli, podaci, izvršno okruženje i dashboardi još nisu
implementirani; projekt se u ovoj fazi ne pokreće kao aplikacija.

## Predložene tehnologije

| Namjena | Alat | Status |
| --- | --- | --- |
| Transformacije i provjere podataka | dbt Core ili SQLMesh | Tim bira jedan alat |
| Vizualizacija i izvještaji | Apache Superset | Predložen opisom zadatka |
| Izvještajna baza | SQL baza kompatibilna s odabranim alatima | Odabir u sljedećoj fazi |
| Verzije koda i suradnja | Git i GitHub | Repozitorij je postavljen |

Aktualne napomene za 2026. godinu i službeni izvori nalaze se u
[tehnološkim smjernicama](docs/technology.md). Ovaj commit ne instalira pakete
niti propisuje neprovjerene kombinacije verzija.

## Planirani tok podataka

```text
Izvorni podaci → staging → intermediate → marts → Apache Superset
```

- `staging`: čišćenje podataka, usklađivanje naziva i tipova stupaca.
- `intermediate`: povezivanje izvora i zajednička poslovna pravila.
- `marts`: završne činjenice, dimenzije i agregacije za izvještavanje.

## Početni pokazatelji

- Neto prihod od prodaje.
- Broj realiziranih narudžbi.
- Neto prodana količina.
- Prosječna vrijednost narudžbe.
- Promjena prihoda u odnosu na prethodni period.

Početne definicije i otvorene odluke opisane su u [katalogu KPI-ja](docs/kpis.md).
Definicije će se uskladiti s dostupnim podacima prije implementacije modela.

## Struktura repozitorija

```text
EP2627-Tim5/
├── data/
│   ├── raw/                 # Lokalni izvorni podaci; sadržaj se ne verzionira
│   ├── processed/           # Lokalni rezultati obrade; sadržaj se ne verzionira
│   └── samples/             # Mali sintetički ili anonimizirani primjeri
├── docs/
│   ├── kpis.md              # Početne definicije pokazatelja
│   └── technology.md        # Odabir alata i upravljanje verzijama
├── models/
│   ├── staging/
│   ├── intermediate/
│   └── marts/
├── scripts/                 # Buduće skripte za učitavanje i pomoćne zadatke
├── superset/
│   ├── dashboards/          # Budući izvozi dashboarda
│   └── datasets/            # Buduće definicije skupova za izvještavanje
├── tests/                   # Buduće provjere modela i kvalitete podataka
├── .editorconfig
├── .gitattributes
├── .gitignore
└── README.md
```

Datoteke `.gitkeep` čuvaju prazne direktorije u Gitu. Struktura je početna
organizacija koda; konfiguracija odabranog alata dodat će se u sljedećoj fazi.

## Preuzimanje projekta

Za ovu fazu potreban je samo Git. U terminalu pokrenuti:

```sh
git clone https://github.com/University-of-Zenica/EP2627-Tim5.git
cd EP2627-Tim5
git status
```

Upute za instalaciju alata i pokretanje modela dodat će se zajedno s izvršnom
konfiguracijom, nakon izbora baze i alata za transformacije.

## Timski rad

1. Za svaki zadatak otvoriti zasebnu granu, npr. `feat/sales-staging`.
2. Koristiti kratke commit poruke s prefiksima `chore:`, `feat:`, `fix:`,
   `docs:` ili `test:`.
3. Promjene slati kroz pull request uz kratak opis i način provjere.
4. Prije spajanja u `main` zatražiti pregled drugog člana tima.
5. Uz promjenu poslovnih pravila ažurirati dokumentaciju i odgovarajuće provjere.

Lozinke, lokalne konfiguracije i stvarni prodajni podaci ne dodaju se u Git.
Za primjere koristiti `data/samples/`; za lokalne ulazne podatke `data/raw/`.
Superset izvoze pregledati prije commita i ukloniti pristupne podatke i osjetljive vrijednosti.

## Sljedeći koraci

- Odabrati izvor podataka, SQL bazu i jedan alat za transformacije.
- Dodati konfiguraciju okruženja s točnim verzijama i primjerima bez tajnih podataka.
- Definirati granularnost prodaje, ključeve te pravila za povrate i otkazivanja.
- Implementirati SQL modele i provjere kvalitete podataka.
- Povezati Apache Superset i izraditi dashboard ključnih pokazatelja.
