# Skolų valdymas – Power Apps stiliaus prototipas

Parengta pagal 2026-11-03 komercinio pasiūlymo skolų aplikacijai funkcionalumą. Tai naršyklėje veikiantis demonstracinis prototipas, o ne importuojamas Power Apps .msapp sprendimas.

## GitHub Pages

1. Išskleiskite ZIP kompiuteryje.
2. Savo GitHub saugyklos pagrindiniame kataloge įkelkite **index.html**. Jis turi būti šaknyje, o ne papildomame aplanke. Galite kartu įkelti README.md ir CSV pavyzdžius.
3. Saugyklos Settings → Pages → Build and deployment pasirinkite „Deploy from a branch“.
4. Pasirinkite šaką „main“, aplanką „/ (root)“, spauskite Save.
5. Kai GitHub paskelbs svetainę, atverkite Pages skiltyje pateiktą nuorodą.

Nereikia npm, build komandos, API raktų ar papildomų bibliotekų. Visi stiliai ir kodas įtraukti į index.html, todėl veikia ir projekto poaplankyje. Vietinei demonstracijai galima tiesiog atidaryti index.html naršyklėje. Duomenų išsaugojimas atidarius per file:// priklauso nuo naršyklės; patikimiausia naudoti GitHub Pages.

## Demonstravimo seka

1. Pradinis vaidmuo – vadybininkė Aistė. „Mano skolininkai“ rodo tik jai priskirtus klientus.
2. Atidarykite skolininko kortelę: skola, paskutinis mokėjimas, importo pokyčiai, priminimų istorija.
3. Sąraše pažymėkite kelis skolininkus → „Paruošti priminimą“ → peržiūrėkite individualius laiškus → pažymėkite patvirtinimą → „Patvirtinti ir siųsti (demo)“.
4. Atidarykite „Priminimų istorija“. Užfiksuotas laikas, gavėjas, skolos suma, etapas, patvirtinęs vadybininkas, laiško turinys ir dabartinės skolos pokytis nuo priminimo.
5. Viršuje pasirinkite „Vadovas“. Matomi visi skolininkai, skolos pagal vadybininkus, filtrai ir visų priminimų istorija. Siuntimo veiksmų nėra.
6. Pasirinkite „Administratorius“ → „Duomenų importas“ → „Imituoti kasdienį importą“ arba įkelkite CSV. Patikrinto CSV pakeitimai įrašomi tik patvirtinus importą.
7. Peržiūrėkite skolininko kortelę po importo: skola pasikeitė, ankstesni priminimai išliko.
8. „Administravimas“: sukurkite naudotoją, aktyvuokite / išjunkite prieigą, priskirkite skolininkus vadybininkams, keiskite laiško šabloną ir etapus.
9. Prieš kitą demonstraciją: „Administravimas“ → „Atkurti demonstracinius duomenis“.

Vaidmenų perjungiklyje yra dvi vadybininkų paskyros, vadovas ir administratorius. Naujus vadybininkus galima sukurti ir jiems priskirti klientus; prisijungimo perjungiklis demonstruoja iš anksto parinktas paskyras.

## Pasiūlymo funkcijų atitiktis

| Funkcija | Prototipo įgyvendinimas |
|---|---|
| Kasdienis CSV atnaujinimas | Tikras CSV nuskaitymas, patikra, importo patvirtinimas, istorija; kasdienio paleidimo imitacija |
| Skolininkų priskyrimai | Administravimo registras, keičiamas vadybininkas |
| Vadybininko asmeninis sąrašas | Vaidmeniui priklausanti duomenų atranka |
| Paieška ir filtravimas | Pavadinimas, kodas, el. paštas, būsena, vadybininkas |
| Skolininko kortelė | Skola, terminas, mokėjimas, pokyčiai, priminimų istorija |
| Skolos ir mokėjimo pokyčiai | Palyginimas su ankstesniu importu, datuoti pokyčiai |
| Skolininkų pasirinkimas | Individualus ir masinis žymėjimas |
| Priminimo peržiūra | Individualus laiškas kiekvienam klientui, tema ir redaguojamas tekstas |
| Vadybininko patvirtinimas | Privaloma patvirtinimo varnelė, atskiras siuntimo veiksmas |
| El. laiškų siuntimas | Imitacija; realių laiškų nesiunčia |
| Siuntimo istorija | Data, gavėjas, skolos suma, etapas, patvirtinęs asmuo, laiškas |
| Vadovo prieiga | Visų klientų ir vadybininkų apžvalga bei istorija |
| Administravimas | Naudotojų prieigos, priskyrimai, šablonas, importo nustatymai |
| Etapų pagrindas | Etapų kūrimas / redagavimas, dienų slenkstis ir aktyvumas; siuntimo metu pasirenkamas etapas |

## CSV formatas

UTF-8, skyriklis kabliataškis arba kablelis. Kabutėmis apgaubti laukai palaikomi. Failo riba – 2 MB.

Privaloma antraštė:

kliento_kodas;pavadinimas;el_pastas;vadybininko_id;skola;terminas;paskutinis_mokejimas;mokejimo_suma

Datos: YYYY-MM-DD. Skolos ir mokėjimo sumos negali būti neigiamos. Dešimtainė dalis gali būti atskirta tašku arba kableliu (kai CSV skyriklis – kabliataškis). Paskutinio mokėjimo data gali būti tuščia. Kodai – raidės, skaičiai, _ arba -; tame pačiame faile nesikartoja. Vadybininkų ID: a – Aistė, m – Mantas, r – Rūta. Visi laukai ir verslo taisyklės yra demonstraciniai: galutiniai derinami pagal realų „Būtentos“ eksportą.

Importas atnaujina pagal kliento kodą ir prideda naujus klientus. Faile nesantys klientai nekeičiami ir nelaikomi apmokėtais; skolos padengimą reikia aiškiai nurodyti eilute su skola 0. Ankstesni priminimai išsaugomi. CSV priskyrimai pakeičia esamus priskyrimus. Blogas failas atmetamas visas, duomenys nekeičiami.

Failai:

- butenta_pavyzdys.csv – pradinė struktūra ir trys klientai.
- butenta_po_mokejimo.csv – tie patys klientai po mokėjimo, skirtas palyginimui.

## Demonstracijos ribos

- Duomenys fiktyvūs ir saugomi tik šios naršyklės localStorage; tarp naudotojų ir įrenginių nesidalijami.
- Vaidmenys ir prieigos imituojami kliento pusėje, nėra tikro autentifikavimo. Viešai publikuojamam prototipui naudokite tik demonstracinius duomenis.
- El. laiškai ir Power Automate vykdymas imituojami; automatinis importas uždarius naršyklę nevyksta.
- Nustatytas laikas ir etapų slenksčiai yra demonstracinė konfigūracija, ne automatinio vykdymo taisyklės. Būtinas rankinis priminimo patvirtinimas.
- Skolos pokytis po priminimo yra duomenų palyginimas, o ne įrodymas, kad mokėjimą nulėmė priminimas.
- Vėlavimo atskaitos data fiksuota: 2026-11-03. Naujų veiksmų data ir laikas – dabartinis naršyklės laikas.
- Tikram sprendimui reikalinga Power Apps aplikacija, duomenų saugykla, Microsoft 365 prieigos ir Power Automate srautai.

## Patikra

Patikrinta JavaScript sintaksė, vaidmenų duomenų atranka, neaktyvi prieiga, CSV kabučių apdorojimas ir klaidų atmetimas, importo skolos bei istorijos išlaikymas, priminimo patvirtinimas ir skolos sumos fiksavimas. Naršyklėje patikrinta priminimo peržiūra, patvirtinimas ir istorija, kasdienio importo imitacija bei naudotojo sukūrimas.
