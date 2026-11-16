# Početni katalog prodajnih pokazatelja

Ovo je prijedlog za dogovor tima, a ne implementirana specifikacija.
Nazivi stupaca i konačna pravila ovise o odabranom izvoru podataka.

## Predložene definicije

| Pokazatelj | Početna definicija |
| --- | --- |
| Neto prihod od prodaje | Zbroj iznosa prodajnih stavki nakon popusta i povrata, bez poreza i dostave |
| Broj realiziranih narudžbi | Broj različitih identifikatora realiziranih narudžbi; otkazane se isključuju |
| Neto prodana količina | Prodana količina umanjena za vraćenu količinu |
| Prosječna vrijednost narudžbe | Neto prihod pripisan uključenim narudžbama / broj tih narudžbi |
| Promjena prihoda (%) | `(prihod tekućeg perioda - prihod prethodnog perioda) / prihod prethodnog perioda * 100` |

Kod dijeljenja nulom ili nedostajućeg usporednog perioda prikazati `NULL`
odnosno „nije primjenjivo”. Narudžbe brojati zasebno od njihovih stavki kako
spajanje tablica ne bi višestruko uvećalo broj narudžbi.

## Odluke prije implementacije

- Potvrditi granularnost izvora: narudžba, stavka narudžbe ili transakcija.
- Odrediti statuse koji znače realiziranu prodaju.
- Dogovoriti datum pripisivanja prihoda i povrata te tretman djelomičnih povrata.
- Za prosječnu vrijednost narudžbe uskladiti skup narudžbi u brojniku i nazivniku;
  odrediti uključuju li se potpuno vraćene narudžbe.
- Potvrditi jesu li iznosi već umanjeni za popuste, povrate ili poreze.
- Odrediti valutu izvještavanja i konverziju ako postoji više valuta.
- Dogovoriti vremensku zonu i usporedbu potpunih ili djelomičnih perioda.
- Potvrditi dostupne dimenzije: datum, proizvod, kategorija, kupac i regija.

## Planirane provjere podataka

- Jedinstvenost ključa prodajne stavke i obavezne vrijednosti ključeva.
- Veze prodaje s dimenzijama proizvoda, kupca i datuma.
- Dopušteni statusi narudžbi i ispravno evidentirani povrati.
- Usklađenost agregiranih iznosa s izvornim podacima.
