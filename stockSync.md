#stockSync – posodobi zalogo artiklov v spletni trgovini
Opis : Metakocka preverja na vsakih 30 sekund spremembe zaloge, ter to informacijijo sporoči spletni trgovini. Akcijo pa lahko sproži tudi uporabnik sam, kjer se prenese trenutno stanje zaloge za vse artikle, ki so označeni za sinhronizacijo.


URL : [eShop_url_base]/items/{item_id}

**Primer klica na strežnik spletne trgovine**
```javascript
{
   "stock_amount" : 12.5
}
```

| Atribut | Obvezen? | V MK | Tip / max dolžina | Opomba |
| ------- | -------- | ---- | ----------------- | ------ |
| stock_amount | DA | zaloga | Decimal | trenutna zaloga artikla v Metakocki

**Opombe**
- {item_id} je lahko id artikla v vaši trgovini ali pa "Šifra artikla" v Metakocki. Za uporabo vaših identifikatorjev je pred tem potrebna sinhronizacija artiklov.



**Primer odgovora spletne trgovine**
```javascript
{
    "id":{item_id},
    ...
}

| Atribut | Obvezen? | V MK | Tip / max dolžina | Opomba |
| ------- | -------- | ---- | ----------------- | ------ |
| id | DA | **/Šifra artikla | String / 30 | ** odvisno od nastavitev

**Opombe**
- spletna trgovina lahko vrne tudi druge parametre
