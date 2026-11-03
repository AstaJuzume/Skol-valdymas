# Skolų valdymas – atnaujintas Power Apps stiliaus prototipas

Versija 2. Parengta pagal pateiktą atnaujintą 2026-11-03 komercinį pasiūlymą. Tai veikiantis HTML demonstracinis prototipas, ne importuojamas Power Apps .msapp failas.

## GitHub Pages: įkėlimas arba atnaujinimas

1. Išskleiskite ZIP kompiuteryje.
2. Saugyklos pagrindiniame kataloge įkelkite arba pakeiskite **index.html**. Failas turi būti šaknyje, ne papildomame aplanke. Galima kartu įkelti kitus paketo failus.
3. Settings → Pages → Deploy from a branch → main → / (root) → Save.
4. Atverkite GitHub pateiktą svetainės nuorodą. Atnaujinus esamą prototipą, palaukite sėkmingo GitHub paskelbimo ir prireikus paspauskite Ctrl+F5.

Nereikia npm, build proceso, API raktų ar išorinių bibliotekų. Viskas, įskaitant PDF šriftą, įtraukta į index.html. Veikia ir GitHub projekto poaplankyje. Galima atverti index.html tiesiog kompiuteryje; duomenų išsaugojimas per file:// priklauso nuo naršyklės.

Versija 2 naudoja atskirą naršyklės duomenų raktą, todėl senos demonstracijos įrašai nepakeičia naujo modelio. Tai nesusiję su tikrų duomenų migracija.

## Kas pasikeitė

| Pasiūlymo funkcija | Prototipe |
|---|---|
| Bendra ir pradelsta skola | Atskiri rodikliai, skaičiuojami pagal sąskaitų likučius ir terminus |
| Per dieną gauti mokėjimai | Pasirenkama diena, faktinių demonstracinių mokėjimų suma ir nuoroda į registrą |
| Sąskaitų registras | Numeris, klientas, vadybininkas, išrašymo data, terminas, suma, likutis, būsena |
| Paieška ir filtrai | Pagal vadybininką, klientą, sąskaitą ir mokėjimo terminų laikotarpį |
| Mokėjimų registras | Atskiri mokėjimai, data, suma, klientas ir susijusi sąskaita; datų ir vadybininko filtrai |
| Kliento kortelė | Skolos informacija, sąskaitos, mokėjimų istorija, importo pokyčiai ir priminimai |
| Vadybininko prieiga | Tik priskirti klientai, sąskaitos, mokėjimai ir ataskaitos |
| Vadovo prieiga | Visų vadybininkų skolų, mokėjimų ir priminimų peržiūra |
| Rankinis priminimų pasirinkimas | Vieno arba kelių skolininkų žymėjimas, individualių laiškų peržiūra |
| Trys priminimų etapai | Mandagus priminimas; raginimas atsiskaityti; galutinis perspėjimas apie galimą teisinį išieškojimą |
| Patvirtinimas prieš siuntimą | Privaloma patvirtinimo varnelė; pakeitus etapą ar laiško tekstą tvirtinama iš naujo |
| Priminimų istorija | Data, etapas, gavėjas, skola, patvirtinęs asmuo, laiško tekstas ir sąskaitų kopija siuntimo metu |
| Skolos pokytis po priminimo | Lyginami to paties siuntimo metu užfiksuoto sąskaitų rinkinio likučiai |
| Individualus PDF | Tikras naršyklėje generuojamas PDF su lietuviškomis raidėmis ir puslapiavimu |
| PDF du kartus per savaitę | Nustatomos dvi skirtingos dienos ir laikas, vieno paleidimo imitacija, ataskaitos kiekvienam aktyviam vadybininkui |
| PDF siuntimo istorija | Ataskaitos duomenų kopija siuntimo metu; vėlesni importai jos nekeičia |
| Administravimas | Prieigos, vadybininkų priskyrimai, trijų etapų šablonai, importo ir PDF grafikas |
| CSV importas | Sąskaitų ir mokėjimų eilutės, patikra, patvirtinimas, atnaujinimas pagal tipą ir ID, importų istorija |

## Rekomenduojama pristatymo eiga

1. Pradėkite nuo vadybininkės Aistės apžvalgos. Matosi bendra ir pradelsta skola bei pasirinktos dienos mokėjimai.
2. „Sąskaitos“: ieškokite SF-001-01, peržiūrėkite terminus ir likučius, atverkite kliento kortelę.
3. Kortelėje peržiūrėkite sąskaitų bei mokėjimų istoriją. Tarp pavyzdžių yra sąskaitų, kurių terminas dar nesuėjęs.
4. „Mano skolininkai“ pasirinkite vieną arba kelis klientus → „Paruošti priminimą“. Pakeiskite etapą, peržiūrėkite skirtingus tekstus ir individualias sąskaitų sumas, pažymėkite patvirtinimą.
5. „Priminimų istorija“ parodo pasirinktą etapą, laiką, gavėją ir užfiksuotą skolą. Siuntimas imituojamas.
6. „PDF ataskaitos“ → „Atsisiųsti PDF“. Vadybininkui pasiekiama jo individuali pradelstų sąskaitų ataskaita.
7. Viršuje pasirinkite „Vadovas“: bendra situacija, visų vadybininkų pjūviai ir registrai.
8. Pasirinkite „Administratorius“: įkelkite butenta_pavyzdys.csv, paskui butenta_po_mokejimo.csv. Patvirtinkite importus. Mokėjimas registruojamas, skola sumažėja, priminimų istorija išlieka.
9. „PDF ataskaitos“ → „Imituoti vieną suplanuotą siuntimą“. Istorijoje sukuriama atskira ataskaita kiekvienam aktyviam vadybininkui. Iš istorijos atsisiunčiamas tuometinės situacijos PDF.
10. „Administravimas“: pakeiskite trijų etapų šablonus, dvi PDF siuntimo dienas, prieigas ir priskyrimus. Prieš kitą pristatymą atkurkite pradinius duomenis.

Viršuje galima demonstruoti dviejų vadybininkų, vadovo ir administratoriaus prieigas. Naujus vadybininkus galima įtraukti ir jiems priskirti klientus; prisijungimo perjungiklyje pateiktos iš anksto numatytos paskyros.

## CSV – naujas formatas

Ankstesnio prototipo CSV formatas nebetinka. Galutinis „Būtentos“ formatas derinamas projekto metu; čia pateikta demonstracinė struktūra:

tipas;iraso_id;kliento_kodas;pavadinimas;el_pastas;vadybininko_id;data;terminas;suma;likutis;saskaitos_id

| Laukas | Sąskaitos eilutė | Mokėjimo eilutė |
|---|---|---|
| tipas | saskaita | mokejimas |
| iraso_id | Unikalus sąskaitos numeris | Unikalus mokėjimo numeris |
| kliento_kodas | Kliento kodas | Kliento kodas |
| pavadinimas, el_pastas, vadybininko_id | Privalomi kliento duomenys | Tie patys kliento duomenys |
| data | Išrašymo data | Mokėjimo data |
| terminas | Apmokėjimo terminas | Tuščias |
| suma | Visa sąskaitos suma | Mokėjimo suma |
| likutis | Neapmokėta dalis, įskaitant 0 | Tuščias |
| saskaitos_id | Tuščias | Susieta sąskaita arba tuščias, jei nesusieta |

UTF-8, kabliataškis arba kablelis; kabutėmis apgaubti laukai palaikomi. Datos YYYY-MM-DD. Failo riba – 2 MB. ID turi sudaryti raidės, skaičiai, _ arba -. Vadybininkų ID: a – Aistė, m – Mantas, r – Rūta. Dublikatų viename faile, nesutampančių to paties kliento duomenų, neigiamų sumų, neteisingų datų ir pažeistų sąskaitų ryšių patikra vykdoma prieš įrašant pakeitimus.

Pakartotinai importuojamas tas pats mokėjimo ID atnaujina įrašą, nesukuria antro. Skola gaunama iš sąskaitos likučio, todėl mokėjimai iš jos antrą kartą neatimami. Faile nesantys įrašai išsaugomi. Sąskaitos apmokėjimą reikia nurodyti jos likučiu 0. Importo vadybininkų priskyrimai atnaujina esamus.

- butenta_pavyzdys.csv – pradinės 24 sąskaitos ir 18 mokėjimų.
- butenta_po_mokejimo.csv – pirmos sąskaitos likutis sumažintas 2 000 EUR ir pridėtas atskiras 2 000 EUR mokėjimas.

## Demonstracijos ribos

Tai statinis prototipas su fiktyviais duomenimis. Duomenys saugomi tik naršyklės localStorage, tarp įrenginių nesidalijami. Vaidmenys imituojami, nėra tikro Microsoft 365 autentifikavimo. Naudokite tik demonstracinius duomenis.

PDF generavimas veikia; el. laiškai tikriems gavėjams nesiunčiami. Kasdienis CSV importas ir PDF siuntimo grafikas automatiškai nevykdomi, parodoma jų eiga rankiniu paleidimu. Tikram veikimui reikėtų Power Apps, Power Automate, duomenų saugyklos ir Microsoft 365 prieigų.

Vėlavimui ir pradelstai skolai naudojama fiksuota 2026-11-03 data. Mokėjimų dieną galima pasirinkti. Nauji veiksmai žymimi dabartiniu naršyklės laiku. Savaitės dienos, valandos, etapų slenksčiai ir laiškų tekstai yra demonstraciniai, tikslinami projekto metu. Automatinio etapų keitimo nėra.

Mokėjimų istorija demonstruoja turimą laikotarpį, nėra pilna buhalterinė apskaita. Skolos pokytis po priminimo rodo likučių palyginimą, ne priežastinį ryšį su siuntimu.

## Patikra

Patikrinti vaidmenų duomenų apribojimai, sąskaitų ir mokėjimų modelis, CSV pakartotinis importas be mokėjimų dubliavimo, klaidingų duomenų atmetimas, skolos ir priminimo istorijos išlaikymas, trečias priminimo etapas, ataskaitų atranka pagal vadybininką ir istorinių kopijų nekintamumas. PDF turinys patikrintas tekstu ir vizualiai, įskaitant kelių puslapių atvejį. Naršyklėje patikrinta sąskaitų paieška, kliento istorija, etapų keitimas ir PDF siuntimo demonstracija.

Įtrauktas DejaVu Sans Mono šriftas; licencija pateikta FONT_LICENSE.txt.
