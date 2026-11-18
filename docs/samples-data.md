# Testni skup podataka o prodaji

## 1. Opis

Ovaj direktorij sadrži sintetičke testne podatke pripremljene za potrebe projekta „Izrada izvještajnog modela s ključnim pokazateljima prodaje“ (EP2627-Tim5).

Podaci su namijenjeni za razvoj, testiranje i provjeru SQL transformacija, kvaliteta podataka i izračunavanja ključnih pokazatelja uspješnosti prodaje (KPI).

Svi podaci o kupcima, proizvodima i narudžbama su izmišljeni i koriste se isključivo u akademske svrhe.

## 2. Struktura skupa podataka

Testni skup podataka sastoji se od četiri CSV datoteke:

### 2.1. customers.csv – Kupci

Sadrži osnovne informacije o kupcima.

Kolone:
- `customer_id` – Jedinstveni identifikator kupca.
- `first_name` – Ime kupca.
- `last_name` – Prezime kupca.
- `email` – Email adresa kupca.
- `city` – Grad u kojem kupac živi.
- `country` – Država kupca.
- `created_at` – Datum registracije kupca.

### 2.2. products.csv – Proizvodi

Sadrži informacije o proizvodima dostupnim za prodaju.

Kolone:
- `product_id` – Jedinstveni identifikator proizvoda.
- `product_name` – Naziv proizvoda.
- `category` – Kategorija kojoj proizvod pripada.
- `unit_price` – Jedinična cijena proizvoda.
- `is_active` – Oznaka koja pokazuje da li je proizvod aktivan.

### 2.3. orders.csv – Narudžbe

Sadrži informacije o narudžbama koje su kreirali kupci.

Kolone:
- `order_id` – Jedinstveni identifikator narudžbe.
- `customer_id` – Identifikator kupca koji je napravio narudžbu.
- `order_date` – Datum kreiranja narudžbe.
- `status` – Status narudžbe.

Mogući statusi narudžbi:
- `completed` – Realizovana narudžba.
- `cancelled` – Otkazana narudžba.
- `pending` – Narudžba na čekanju.

### 2.4. order_items.csv – Stavke narudžbi

Sadrži informacije o pojedinačnim proizvodima koji se nalaze unutar narudžbi.

Kolone:
- `order_item_id` – Jedinstveni identifikator stavke narudžbe.
- `order_id` – Identifikator narudžbe kojoj stavka pripada.
- `product_id` – Identifikator kupljenog proizvoda.
- `quantity` – Količina kupljenog proizvoda.
- `unit_price` – Jedinična cijena proizvoda u trenutku kupovine.
- `discount_amount` – Iznos popusta na stavku narudžbe.

## 3. Način povezivanja podataka

Podaci su organizovani u četiri međusobno povezane cjeline.

- Jedan kupac može imati više narudžbi.
- Jedna narudžba može sadržavati više stavki.
- Svaka stavka narudžbe odnosi se na jedan proizvod.
- Svaka narudžba pripada jednom kupcu.

Povezivanje se ostvaruje pomoću identifikatora (ID vrijednosti) koji predstavljaju primarne i strane ključeve.

## 4. Konvencije i format podataka

Prilikom pripreme testnih podataka korištena su sljedeća pravila:

- Valuta: BAM (konvertibilna marka).
- Format datuma: `YYYY-MM-DD`.
- Decimalni separator: tačka (`.`).
- Format datoteka: CSV.
- Kodiranje znakova: UTF-8.

## 5. Poslovna pravila

Za potrebe početnog izvještajnog modela definisana su sljedeća pravila:

- U obračun realizovanog prihoda ulaze samo realizovane narudžbe (`completed`).
- Otkazane narudžbe (`cancelled`) ne ulaze u obračun realizovanog prihoda.
- Narudžbe na čekanju (`pending`) ne ulaze u obračun realizovanog prihoda.
- Neto prihod pojedinačne stavke računa se prema formuli:

  `quantity * unit_price - discount_amount`

- Povrati proizvoda nisu obuhvaćeni početnim testnim skupom podataka.

## 6. Provjera kvaliteta podataka

Prilikom provjere ispravnosti podataka potrebno je osigurati:

- Jedinstvenost vrijednosti primarnih ključeva.
- Ispravnost veza između primarnih i stranih ključeva.
- Postojanje svih referenciranih kupaca, proizvoda i narudžbi.
- Pozitivne vrijednosti količina proizvoda.
- Nenegativne vrijednosti cijena i popusta.
- Ispravan format datuma.

## 7. Namjena testnih podataka

Pripremljeni testni podaci predstavljaju početni izvor za daljnji razvoj izvještajnog modela prodaje.

Koristit će se za:

- Izradu staging modela.
- Povezivanje i transformaciju podataka.
- Kreiranje dimenzijskih i činjeničnih tabela.
- Izračunavanje ključnih pokazatelja prodaje (KPI).
- Testiranje kvaliteta i ispravnosti podataka.
- Izradu interaktivnih izvještaja i dashboarda u Apache Supersetu.

Ovaj skup podataka predstavlja početnu osnovu za razvoj i testiranje izvještajnog modela.
