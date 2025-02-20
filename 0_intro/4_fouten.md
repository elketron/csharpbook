# Fouten oplossen

![](../assets/attention.jpg)

Je code kan niet gecompileerd en uitgevoerd worden zolang er fouten in je code staan (dit bespraken we reeds in [een eerder hoofdstuk](0_intrototcs.md)).

Indien je op de groene start knop duwt en volgende waarschuwing krijgt **KLIK DAN NOOIT OP YES EN DUIDT NOOIT DE CHECKBOX AAN**:
![Zie je de fout?](../assets/0_intro/errorwarning.PNG)
>De eerste die dit wél doet trakteert de hele klas als ik dit ontdek.

> Lees de boodschap eens: wat denk je dat er gebeurt als je op 'yes' duwt? Inderdaad, VS zal de laatste goed gelukte code uitvoeren en dus niet de code die je nu hebt staan waarin nog fouten staan.

## Fouten vinden

Zolang er dus fouten in je code staan moet je deze eerst oplossen voor je verder kan. Gelukkig helpt VS je daarmee op 2 manieren:

* Fouten in code worden met een rode squigly onderlijnt.
* Onderaan zie je in de statusbalk of je fouten hebt.

![Zie je de fout?](../assets/0_intro/error.PNG)

## Fouten vinden

Uiteraard ga je vaak code hebben die meerdere schermen omvat. Je kan via de error-list snel naar al je fouten gaan. Open deze door op het error-icoontje onderaan te klikken:

![De errorlist](../assets/0_intro/errorlist.PNG)

In deze list kan je nu op iedere error klikken om ogenblikkelijk naar de correct lijn te gaan.

## Fouten oplossen

Wanneer je je cursor op een lijn met een fout zet dan zal je soms vooraan een geel error-lampje zien verschijnen:

![Lampje](../assets/0_intro/errorlampje.png)

Je kan hier op klikken en heel vaak krijg je dan ineens een mogelijke oplossing. **Wees steeds kritisch** hierover want VS is niet alomwetend en kan niet raden wat je altijd bedoelt. Neem dus het voorstel niet zomaar over zonder goed na te denken of het dat was wat je bedoelde.

## Meest voorkomende fouten

De meest voorkomende fouten in deze eerste weken zullen zijn:

* **Kommapunt** vergeten.
* **Schrijffouten** in je code RaedLine i.p.v. ReadLine.
* Geen rekening gehouden met **hoofdletter gevoeligheid** Readline i.p.v. ReadLine (zie volgende hoofdstuk).
* Per ongeluk **accolades verwijderd**.
* Code geschreven op plekken waar dat niet mag (je mag enkel binnen de accolades van ``Main`` schrijven).
