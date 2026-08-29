# Metodologie

`archdex` este un registru construit **manual, articol cu articol**, din [categoria Arhitectură a revistei igloo.ro](https://igloo.ro/category/arhitectura/) (171 de pagini, ~9 articole/pagină, ordonate cronologic invers), cu verificarea directă a dreptului de semnătură în [Tabloul Teritorial București al OAR](https://www.oar-bucuresti.ro/tabloul/).

Toate datele sunt în `index.html`, în array-ul JavaScript `DATA`.

## Stadiu curent

- **Pagini parcurse:** 1–85 din 171 (la nivel de titlu, integral).
- **~230 de articole** deschise integral pentru extragerea creditelor de arhitectură.
- **115 studiouri** în registru: 108 românești + 7 internaționale.
- Verificare OAR București făcută pe literele: A, B, C, D, G, K, L, M, N, P, R, S, Ș, W, Z.
- Rundă nouă începe cu **pagina 86**.

## Pași, pentru fiecare pagină de categorie

1. Se citesc titlurile celor ~9 articole. Se marchează drept „probabil românesc" cele cu oraș/județ românesc în titlu **sau** fără nicio țară menționată explicit; drept „internațional, skip" cele cu țară/oraș străin clar în titlu.
2. Se deschid **doar** candidatele românești. Se caută caseta tehnică de la finalul articolului (începe de obicei cu `PROIECT:` sau `ARHITECTURĂ:`) — de acolo: numele studioului, arhitecții nominal, amplasamentul, tipul de proiect, colaboratorii, anul finalizării, premiile.
3. Articolele care sunt doar interviu/eveniment fără proiect construit cu adresă clară **nu** se adaugă ca studio nou — se trec în secțiunea Excluderi de mai jos.
4. Pentru fiecare arhitect nou se încearcă o verificare în Tabloul OAR București (`.../tabloul/arhitecti/{litera}/`). Dacă nu apare acolo: `verified: null` + notă „posibil altă filială județeană". Dacă apare dar cu drept de semnătură suspendat: `verified: false` + notă.
5. Studio nou → obiect nou în `DATA`, cu structura exactă a obiectelor existente.
6. Studio deja existent cu un proiect nou → proiectul se adaugă în `notable[]` al intrării existente. Nu se dublează intrarea.
7. Se actualizează `renderStats()` și numărul de pagini din acest fișier.

## Reguli de calitate

- Nu se inventează date. Fără CUI, an de înființare sau recenzii → se scrie explicit „Neverificat" / „necunoscută — de verificat".
- Din pagina 21 înainte, articolele clar internaționale (țară/oraș străin în titlu) au fost sărite fără a fi deschise, pentru optimizare. Pagini integral (sau aproape integral) internaționale până acum: 44, 46, 47, 50, 56, 58, 63, 73 (parțial), 74, 79 (parțial), 85 (parțial). Începând cu ~pagina 60 (arhivă 2019–2020, era pandemică), densitatea de studiouri românești noi scade — mai multe eseuri speculative, roundup-uri „igloo likes", serii de portret „A≤40" și interviuri de fotografi.
- Date de firmă căutate pe termene.ro / listafirme.eu — CUI confirmat doar unde denumirea a permis identificare certă.

## Limitări

- Studiourile din afara Bucureștiului pot fi înregistrate la alte filiale teritoriale OAR, neverificate încă aici.
- Recenziile publice (Google/Facebook) sunt rare pentru birouri mici B2B — absența lor nu e neapărat un semnal negativ.
- Site static, un singur fișier — pentru date noi se rulează o rundă nouă de extragere.
- Câteva intrări sunt fundații sau persoane fizice, nu birouri comerciale clasice (Pro Patrimonio, WeWilder, Jan Hülsemann, ABRAL) — marcate ca atare în notă.

## Excluderi (articole parcurse, dar neadăugate)

Interviuri / profiluri / eseuri fără proiect construit cu adresă:

- Atelier TERRApia (practică de cercetare/educație)
- Interviuri: Ilinca Păun Constantinescu, Adrian Phiffer, Oana Stănescu, Ștefan Davidovici, Anda Ștefan, Raluca Șoaita, Iulia Stanciu, Bogdan Anghel, VATRAA, iungo studio, Marcos Cruz, Nathalie de Vries (MVRDV)
- Serii de portret „A≤40" (fără proiect documentat cu adresă): Silviu Mihăilescu, Studio 1408, LAMA Arhitectura, Bogdan Ciocodeică Studio
- Interviuri de fotografi de arhitectură: Mihai Caranica, Radu Matei, Alexandra Bendea, Arthur Țințu, Cristi Radu; studiouri de vizualizare: bucharest.studio, Panoptikon, viewcatchers
- Interviu „Arhitectura în vremea COVID-19: Ioka Design și Studio3plus"
- Eseuri istorice (fără intervenție contemporană cu echipă nominalizată): Ioana Grigorescu, Henrieta Delavrancea-Gibory
- Reactivarea culturală a Așezămintelor Ion I. C. Brătianu (ARCEN) — fără birou de proiectare nominalizat
- Pavilionul BIT.BIO.BOT (Bienala de la Veneția 2021)
- Guesthouse-uri săsești restaurate de arhitecți străini individuali, fără birou (Casa Noah / Paul Hemmerth, Casa Albă Viscri / Werner Desimpelaere)
- Școala de la Piscu (inițiativă artistică Adriana și Virgil Scripcariu; credit de arhitectură subțire — arh. Cristian Bălan)
- Concepte / pavilioane temporare fără birou nominalizat (Seed House / Metropolis, Nuba – Mamaia, birouri-container Therme)
- Dosare / eseuri tematice igloo (ex. „Dosar #210 — Pe Topolog, în sus")

## Cum se extinde

- Rundă nouă începând cu **pagina 86 din 171**.
- Fiecare studio nou = obiect în `DATA` din `index.html`.
- Verificarea OAR se face pe tablourile teritoriale publice (București sau alte filiale județene).

## Surse

Compilat din igloo.ro (articolele sunt citate în fiecare fișă) · oar-bucuresti.ro/tabloul · termene.ro / listafirme.eu · anuala.ro · site-urile proprii ale studiourilor.

**Document de cercetare personală — nu constituie recomandare profesională sau juridică.**
