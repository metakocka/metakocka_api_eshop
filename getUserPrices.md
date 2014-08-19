#getUserPrices – vrne seznam cen za podanega uporabnika
Opis : Iz Metakocke lahko za posameznega partnereja, na podlagi njegovega e-poštnega naslova in seznama artiklv, pridobimo podatke o ceni ter popustu za posamezen artikel.


URL : https://main.metakocka.si/rest/eshop/getUserPrices/{company_id}/{secret_key}/?user={user_email}&items={item:quantity}

**Primer klica **

https://main.metakocka.si/rest/eshop/getUserPrices/123/S252zoQTz6DaOhsxWdJ/?user=example@example.com&items=13:1,51:50

| Atribut | Obvezen? | V MK | Tip / max dolžina | Opomba |
| ------- | -------- | ---- | ----------------- | ------ |
| company_id | DA | Identifikator podjetja | Long | 
| secret_key | DA | Token | String | Definira se ga v nastavitvah za "Spletne povezave"
| user | DA | email partnerja | String | Definira se ga na kontaktih partnerjev (kupcev)
| items | DA | Šifra artika : zaloga | String : Decimal | Seznam artiklov s količino ločenih z vejcio. Med šifro artika in količino je dvopičje (:).



**Primer odgovora**
```xml
<xml version="1.0" encoding="UTF-8"?>
<pricesInfo>
 <user userID="160000001"></user>
 <itemList>
   <item itemID="AP-001">
     <price currency="EUR" discountApplied="16%">123.50</price>
   </item>
   <item ...>
     ...
   </item>
   ...
 </itemList>
</pricesInfo>



| Atribut | Obvezen? | V MK | Tip / max dolžina | Opomba |
| ------- | -------- | ---- | ----------------- | ------ |
| item | NE | Artikel | Element | Vsebuje atribut "itemId" - "Šifra artikla"
| price | DA | Cena | Decimal | Cena artikla z vsemi popusti in brez davka.
| price:currency | DA | Valuta | String / 3 | Valuta cene. Za enkrat podprta samo EUR valuta.
| price:discountApplied | NE | Popust | Decimal | Popust, ki je že vštet v ceno.

**Opombe**
- spletna trgovina lahko vrne tudi druge parametre


**Primer odgovora napake**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<error code="secretKey_not_valid" shouldRetry="false">
  Secret key is not valid
</error>
```
