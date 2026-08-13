# vitesterki.no — kom i gang (GitHub + Cloudflare Pages)

Dette tar ca. 30–45 minutter første gang, og aldri igjen.

## 1. GitHub (gratis konto)

1. Opprett konto på github.com (hvis du ikke har).
2. Lag et nytt repository: navn `vitesterki`, sett det til **Public** (eller Private, begge fungerer).
3. Last opp alle filene i denne mappen: klikk «uploading an existing file», dra inn hele innholdet (index.html, om.html, annonselenker.html, style.css og mappen artikler/). Commit.

## 2. Cloudflare Pages (gratis)

1. Opprett konto på cloudflare.com.
2. Gå til **Workers & Pages → Create → Pages → Connect to Git** og velg `vitesterki`-repoet.
3. Ingen build-innstillinger trengs (ren HTML) — bare Deploy. Du får en midlertidig adresse type `vitesterki.pages.dev`. Sjekk at siden vises der.

## 3. Koble domenet

1. I Cloudflare Pages-prosjektet: **Custom domains → Set up a custom domain** → skriv `vitesterki.no`. Cloudflare gir deg instruksjoner.
2. Enkleste vei: legg hele domenet inn i Cloudflare (gratis plan) — Cloudflare gir deg to navnetjenere (f.eks. `xxx.ns.cloudflare.com`).
3. Logg inn hos Domeneshop → ditt domene → DNS/navnetjenere → bytt til Cloudflares to navnetjenere. Det kan ta noen timer før det virker.
4. Legg også til `www.vitesterki.no` som custom domain (redirect til hoveddomenet).

## 4. E-postadressen post@vitesterki.no (gratis)

Cloudflare har gratis **Email Routing**: i Cloudflare-dashbordet for domenet → Email → Email Routing → opprett `post@vitesterki.no` og pek den til Gmail-adressen din. Da virker kontaktadressen på siden uten å kjøpe e-post.

## 5. Publisere en ny artikkel (ukesrutinen)

1. Claude gir deg en ferdig HTML-fil → legg den i `artikler/`-mappen i GitHub-repoet (Add file → Upload).
2. Åpne `index.html` i GitHub (blyant-ikonet), kopier en `<li>`-blokk i «Siste tester»-listen og oppdater tittel/lenke/beskrivelse. Nyeste øverst.
3. Commit. Cloudflare publiserer automatisk i løpet av ~1 minutt. Det er alt.

## 6. Etter at siden er live (én gang)

- **Google Search Console** (search.google.com/search-console): legg til `vitesterki.no`, verifiser via DNS (Cloudflare gjør dette enkelt). Det er her vi følger med på rangeringer.
- **Søk på partnernettverk:** meld deg på Partner-ads først (rask godkjenning), deretter Adtraction. Bruk den nye e-postadressen.
- **Nyhetsbrev:** opprett gratis konto hos MailerLite eller Buttondown, og si fra til Claude — så bytter vi ut den midlertidige påmeldingsknappen med et ekte skjema.

## Filene i denne pakken

- `index.html` — forsiden med artikkelliste og nyhetsbrevboks
- `om.html` — om-siden (har et [TODO] hvor du skriver 2–3 setninger om deg selv)
- `annonselenker.html` — lovpålagt merking av affiliatelenker, ferdig skrevet
- `style.css` — hele designet, lys og mørk modus
- `artikler/beste-ki-verktoy-norsk-tekst.html` — utkast til artikkel #1 med [DIN TEST]-felter
- `INNHOLDSPLAN.md` — de 12 første artiklene, rangert
