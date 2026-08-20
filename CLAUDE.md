# CLAUDE.md — vitesterki.no

Dette er prosjektkonteksten for nettstedet **Vi tester KI** (vitesterki.no).
Les denne før du gjør noe i repoet.

---

## 1. Hva dette er

En norskspråklig testside for KI-verktøy, eid og drevet av Johannes Framnes.
Forretningsmodellen er affiliate: vi tester verktøy selv, skriver ærlige tester, og tjener provisjon
når lesere kjøper abonnement via sporingslenkene våre.

**Mål:** 100.000 kr i akkumulert inntekt. Realistisk horisont: 15–24 måneder.
Hovedinntekten skal komme fra SaaS-verktøy med gjentakende provisjon (20–40 %).

**Redaksjonell kjerneregel:** Vi påstår aldri at vi har testet noe vi ikke har testet.
Testede artikler er hele konkurransefortrinnet — konkurrentene publiserer uprøvd KI-generert innhold.
Research-basert innhold (priser, guider, nyheter) er lov, men skal alltid merkes tydelig. Se punkt 9.

---

## 2. Teknisk oppsett

- Ren statisk HTML. Ingen rammeverk, ingen byggesteg, ingen avhengigheter.
- Hostet på **GitHub Pages** fra `main`-branchen. Push = publisering (ca. 1 minutt).
- Domene: vitesterki.no (også www). DNS hos registraren, A-records mot GitHub Pages.
- Google Search Console er koblet til via TXT-record. Impact-verifisering ligger som meta-tag i `index.html`.

### Filstruktur
```
index.html                 Forside med artikkelliste + nyhetsbrevboks
om.html                    Om oss / testmetodikk
annonselenker.html         Lovpålagt informasjon om affiliatelenker
style.css                  Hele designet, lys + mørk modus
sitemap.xml                Nettstedkart (meldt inn i Search Console)
artikler/*.html            Én fil per artikkel
artikler/bilder/*.png      Skjermbilder til artiklene
```

### Ved publisering av ny artikkel — gjør ALLTID alle fire:
1. Legg HTML-filen i `artikler/`. Filnavn = URL-slug, små bokstaver, bindestrek, ingen æøå
   (f.eks. `beste-transkribering-norsk-tale.html`).
2. Legg til `<li>`-blokk øverst i artikkellisten i `index.html` (nyeste øverst).
3. Legg til `<url>`-blokk i `sitemap.xml` med dagens dato i `<lastmod>`.
4. Legg inn interne lenker: den nye artikkelen lenker til minst én eksisterende, og
   minst én eksisterende artikkel oppdateres med lenke til den nye.

Etter push: minn Johannes på å be om indeksering av den nye URL-en i Google Search Console.

---

## 3. Artikkelmal og struktur

Kopier strukturen fra `artikler/beste-transkribering-norsk-tale.html`. Fast oppbygning:

1. `<div class="disclosure">` øverst hvis artikkelen har annonselenker (lovpålagt merking).
2. `<h1>` + `<p class="lede">` — konklusjonen antydes allerede i ingressen.
3. **Slik testet vi** — metode, dato, hvilke versjoner/gratisnivåer.
4. **Kort oppsummert** — `<table>` med verktøy, tall, styrke, svakhet.
5. Én `<h2>`-seksjon per verktøy, hver avsluttet med `<div class="verdict">`.
6. Konklusjon — hvem bør velge hva. Aldri én universell vinner hvis det ikke er sant.
7. **Ofte stilte spørsmål** — 2–4 `<h3>`-spørsmål.
8. `<p class="tagline">` med «Sist testet: [måned år]».
9. «Les også»-lenke til relatert artikkel.

### Skrivestil
- Norsk bokmål, direkte og konkret. Ingen svulstige adjektiver, ingen KI-klisjeer.
- Alltid både styrke og dokumentert svakhet per verktøy. Ren skryt ødelegger tilliten.
- Siter faktiske feil ordrett fra testen — det er beviset på at vi har testet.
- Aldri påstander vi ikke kan belegge. Fikk vi ikke testet noe, skriver vi det.
- Terningkast/prosenter er lov, men må kunne forsvares mot fasiten.

---

## 4. Testmetodikk

Prinsippet er **fasit-basert testing**: vi lager en kjent fasit, kjører samme input gjennom
alle verktøy, og teller avvik. Da kan vi publisere tall i stedet for synsing.

Etablerte tester så langt:
- **Skriveverktøy:** tre faste oppgaver (purre-e-post, blogginnledning, klarspråk-omskriving).
  Vurderes på idiomatisk norsk, mengde etterarbeid, treffsikker tone.
- **Transkribering:** ett innlest manus (`testmanus`) med kjente feller — beløp i klartekst,
  fakturanummer siffer for siffer, norske egennavn, låneord, sammensatte ord, og et avsnitt
  på vestlandsdialekt/nynorsk. Feil telles på ordnivå, bokmål og dialekt rapporteres separat.

**Norsk-vinkelen er hele moaten.** Test alltid på norske forhold: bokmål, nynorsk, dialekt,
norske egennavn, norske systemer (Fiken, Tripletex, Altinn). Internasjonale testsider kan ikke kopiere dette.

---

## 5. Penger og lenker

- Affiliatelenker skal ALLTID ha `rel="sponsored"` og stå i en `<div class="verdict">`.
- Artikler med slike lenker skal ha disclosure-boksen øverst.
- Aktive programmer: **Happy Scribe** via Impact —
  `https://happyscribe.sjv.io/c/7622866/3148390/39601`
- Plattformer: Impact (godkjent), Partner-ads og Adtraction (søkt/under behandling).
- **Viktig:** ChatGPT, Claude, Gemini og Copilot har ikke partnerprogram for privatkunder.
  Artikler om dem er trafikkbyggere, ikke inntektsartikler. Sikt mot ca. to inntektsartikler
  (verktøy med program) per trafikkartikkel.

---

## 6. Innholdsplan

Publisert:
1. Beste KI-verktøy for å skrive norsk tekst (ChatGPT, Claude, Copilot, Gemini)
2. Transkribering på norsk (Happy Scribe, Notta, Good Tape, NB Whisper)

Neste, rangert etter vinnbarhet × inntektspotensial:
3. Beste KI til møtereferater for norske møter
4. KI for små bedrifter: verktøy vi anbefaler (og de vi dropper)
5. KI til regnskap og faktura for norske bedrifter (Fiken/Tripletex-integrasjoner)
6. Beste gratis KI-verktøy i 2026
7. Er ChatGPT Plus verdt pengene? (norsk vurdering)
8. KI til jobbsøknaden
9. Beste KI-bildegeneratorer testet med norske instruksjoner
10. Nynorsk-testen: hvilke verktøy takler faktisk nynorsk?

Mål: 2–3 artikler i uka. Volum er den viktigste variabelen de første 6 månedene.

---

## 7. Arbeidsdeling

**Johannes gjør:** tester verktøyene, tar skjermbilder, feller dommene, godkjenner før publisering.
**Claude gjør:** utkast, struktur, feilanalyse mot fasit, HTML, interne lenker, sitemap, commit og push.

Johannes er ikke utvikler. Forklar tekniske steg i klartekst, og ikke anta kjennskap til git-terminologi.
Han vil ikke ringe eller kontakte folk — all vekst skal skje gjennom publisering og skriftlige kanaler.

---

## 8. Gjøremål som ligger og venter

- [ ] Bytte ut midlertidig nyhetsbrevknapp i `index.html` med ekte MailerLite-skjema
- [ ] Sette opp e-postvideresending for post@vitesterki.no (f.eks. ImprovMX)
- [ ] Skjermbilder til transkriberingsartikkelen (`artikler/bilder/`)
- [ ] Søke på flere partnerprogrammer i Impact etter hvert som artikler publiseres
- [ ] Fra ca. artikkel 8: LinkedIn-poster gjenbrukt fra publiserte funn
- [ ] Fra ca. måned 6: engelsk versjon av vinnerartikler på datainthemaking.com

---

## 9. To innholdsspor (lagt til august 2026)

Nettstedet har to typer innhold. **Blandingen må aldri viskes ut** — det er tilliten som er hele forretningsmodellen.

### Spor A — testede artikler (2 i uka)
Fasit-basert testing som beskrevet i punkt 4. Merkes «Vi har testet dette selv».
Dette er moaten. Ingen påstand om testing uten faktisk testing — aldri, uansett tidspress.

### Spor B — research-basert innhold (3–4 i uka)
Ærlig, nyttig innhold som ikke krever at vi tester noe. **Skal alltid merkes tydelig øverst**
med en `<div class="disclosure">` som sier hva det er, f.eks.
«Dette er en prisoversikt, ikke en test. Tallene er hentet fra leverandørenes egne prissider i [måned år].»

Godkjente formater i spor B:

| Format | Kilde | Eksempel |
|---|---|---|
| **Prisguide** | Leverandørenes prissider | «Hva koster KI-verktøyene i Norge?» |
| **Forklarende guide** | Faglig kunnskap, dokumentasjon | «Slik velger du transkriberingsverktøy» |
| **Nyheter/lanseringer** | Leverandørens egne kunngjøringer | «Ny norsk språkstøtte i X» |
| **Bruksguide** | Johannes' egen daglige bruk | «Slik får du bedre norsk ut av ChatGPT» |
| **Regelverk/praktisk** | Lovtekst, Skatteetaten, Datatilsynet | «KI og GDPR for norske bedrifter» |
| **Oppsummering av andres funn** | Navngitte, lenkede kilder | «Hva sier forskningen om KI og norsk?» |

**Regler for spor B:**
- Aldri skriv «vi testet» om noe vi ikke har testet.
- Oppgi alltid kilde og dato. Priser og fakta forfaller raskt.
- Norsk merverdi er poenget: omregn til kroner, legg til 25 % mva, forklar hva som gjelder i Norge.
- Lenk alltid til minst én spor A-artikkel — det er der troverdigheten ligger.
- Prisguider oppdateres **månedlig**. Oppdatert dato er både nyttig for leseren og god SEO.

### Forsiden
Overskriften er «Siste fra oss», ikke «Siste tester», nettopp fordi begge spor ligger der.
Spor B-artikler får en `<div class="meta"><strong>Prisoversikt</strong> – ikke en test</div>`-merking i listen.
