# Skolos ir bonusai – Power Apps stiliaus demonstracija

Atnaujinta 2026-11-05 pagal sutartus procesų pakeitimus. Aplikacija veikia iš vieno index.html, paruošta GitHub Pages.

## GitHub Pages atnaujinimas

Išskleiskite ZIP ir saugyklos pagrindiniame kataloge pakeiskite index.html. Paskelbus GitHub Pages atnaujinimą prireikus naudokite Ctrl+F5. Naujos saugyklos nustatymai: Settings → Pages → Deploy from a branch → main → / (root).

Nereikia npm, build, API raktų ar išorinių bibliotekų. PDF šriftas įtrauktas. Tai HTML prototipas, ne Power Apps .msapp sprendimas. Nauja proceso versija pradeda atskirą fiktyvių duomenų demonstraciją, todėl senos naršyklės demonstracijos įrašai nepakeičia naujų grafikų.

## Vienoda prieiga

Vadovas ir jo pavaduotoja turi vienodas funkcijas ir mato visą informaciją. Vaidmenų perjungiklis pašalintas. Vadybininkai – individualių skolų ir bonusų PDF gavėjai, prie aplikacijos nesijungia. Pateikti 25 fiktyvūs vadybininkai.

## Siuntimo eiga

| Gavėjai | Turinys | Kada / kaip |
|---|---|---|
| Visi skolininkai su pradelstomis sąskaitomis | 1 etapo mandagus priminimas | Automatiškai pirmadieniais ir ketvirtadieniais |
| Rankomis pasirinkti skolininkai | 2 etapo raginimas arba 3 etapo galutinis perspėjimas | Pasirenkamas etapas ir el. laiško turinys; siųsti dabar arba pasirinktą datą ir laiką; reikia patvirtinimo |
| Aktyvūs vadybininkai | Individualus jų klientų pradelstų skolų PDF | Automatiškai antradieniais |
| Rankomis pažymėti vadybininkai | Individualus jų skolų PDF | Bet kuriuo metu, vienam arba keliems pažymėtiems gavėjams |
| Vadybininkai su paruoštais bonusų įrašais | Individualus mėnesio bonusų PDF | Kartą per mėnesį pasirinktą kalendorinę dieną |

Skiltyje „Siuntimų grafikai“ galima imituoti 1 etapo automatinį paleidimą. Kalendorinė data turi būti pirmadienis arba ketvirtadienis. Tą pačią grafiko dieną pakartotas paleidimas nedubliuoja priminimų. Suplanuoti 2 ir 3 etapų priminimai saugomi eilėje; galima atšaukti arba imituoti termino atėjimą. Tai aiškiai pažymėta demonstracija, ne tikras ankstyvas laiško siuntimas.

Skolų PDF skiltyje yra atskira vadybininkų atrankos lentelė ir mygtukas „Siųsti pažymėtiems“. Rankinis siuntimas naudoja kiekvieno pažymėto vadybininko visų pradelstų sąskaitų duomenis, nepriklausomai nuo peržiūros filtrų. Siuntimo istorijoje išsaugoma tuometinė individuali ataskaita ir siuntimo tipas.

## Bonusų pildymas ir RPP palyginimas

Pagrindinėje bonuso formoje rodomi pardavimai, RPP, pradelsta skola, mažinimo suma ir išmokamas bonusas. Kaštai, korekcijos ir ketvirčių likučiai išskleidžiami prireikus. Tarpiniai skaičiavimai atitinka pateikto Excel logiką; galutinę išmoką įveda vadovas arba pavaduotoja.

„Plovyklos, remontai ir kt.“ pervadinta į „Kiti kaštai“. Prie sumos galima įrašyti, iš kokių sąnaudų ji susideda. Komentaras išsaugomas įraše ir pateikiamas bonuso PDF.

Bonusų PDF skiltyje ir pačiame PDF pateikiamas 25 vadybininkų RPP pasiskirstymo skritulys. Kiekvienos dalies plotas proporcingas ataskaitinio mėnesio RPP pagal Excel 11 eilutę. Pasirinkto vadybininko dalis atitraukta iš bendro skritulio ir apvesta tamsia riba. Dešinėje jo dalis parodyta atskirame šviesaus fono skritulyje su vardu, RPP suma ir komandos procentu; kampas išlieka proporcingas RPP. Ryškios besikeičiančios spalvos ir baltos ribos aiškiau atskiria visas dalis. Pasirinkti galima iš sąrašo, paspaudus skritulio dalį arba klaviatūros Enter / tarpo klavišu. Vaizdas atnaujinamas vietoje, neperkraunant visos ataskaitos. Tas pats išskyrimas pateikiamas PDF.

Dalys pažymėtos V01–V25; išskleidžiamoje lentelėje ir PDF detalizacijoje pateiktos atitinkamų vadybininkų RPP sumos. RPP nėra galutinis išmokamas bonusas. Jei vadybininkų skaičius pasikeičia, skritulio dalių skaičius prisitaiko. Trūkstamos ir neigiamos RPP reikšmės diagramoje aiškiai pažymimos arba nevaizduojamos; nulinė reikšmė nesukuria klaidingo ploto.

Siuntimo metu išsaugoma bonuso, komentarų ir visos komandos RPP palyginimo kopija. Vėlesni pakeitimai nekeičia istorinio PDF.

## Būtentos API ir skolų informacija

API skiltyje rodoma paskutinio atnaujinimo būsena, grafikas ir vykdymų istorija. Sėkmingo atnaujinimo demonstracijoje gaunama atnaujinta sąskaita bei mokėjimas. Klaidos demonstracijoje ankstesni duomenys išsaugomi. Sąskaitos ir mokėjimai atnaujinami pagal ID, skola gaunama iš sąskaitų likučių. PDF ir priminimų istorija išlieka.

Išlieka skolų apžvalga, dienos mokėjimų rodiklis, klientų, sąskaitų, mokėjimų registrai, paieška bei filtrai pagal vadybininką, klientą, sąskaitą ir laikotarpį.

## Patikra ir ribos

Patikrintos bendros teisės, 1 etapo savaitės dienos ir nedubliavimas, 2 etapo planavimas ir įvykdymas, individualios pažymėtų vadybininkų ataskaitos, 25 proporcingos RPP dalys, kaštų komentarų išlaikymas ir istorinių kopijų nekintamumas. Naršyklėje patikrinta diagrama bei būsimo priminimo planavimas. PDF diagrama patikrinta vizualiai.

Tikras API ryšys, el. laiškai ir automatinis grafiko vykdymas imituojami. PDF generavimas veikia. Uždarius naršyklę foniniai procesai nevyksta. Tikram sprendimui reikalingos serverio integracijos ir siuntimo automatizacijos.

Duomenys fiktyvūs, saugomi tik šios naršyklės localStorage. Tikro autentifikavimo nėra. Ataskaitų skolų ir mokėjimų atskaitos data – 2026-11-05. Nauji veiksmai žymimi dabartiniu naršyklės laiku. Automatinio paleidimo demonstracijos data keičia grafiko dieną, o duomenų rinkinys lieka demonstracinis. Laiko įvestys interpretuojamos pagal naršyklės vietinę laiko juostą; pristatant Lietuvoje naudokite Europe/Vilnius.

DejaVu Sans Mono šrifto licencija pateikta FONT_LICENSE.txt.

RPP vizualizacijos atnaujinimas: pasirinkto žmogaus dalis išskirta atskirai, spalvos kontrastingesnės, ribos storesnės. Patikrinti 25 dalių, tuščio rinkinio, nulinių reikšmių ir vieno vadybininko atvejai; naujas PDF peržiūrėtas vizualiai.
