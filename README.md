# Visit Oslo — Media Omtale

Vue-app for å registrere medieomtale i SuperOffice. Bygget av Cloud Connection.

Single-file HTML-app (Vue 3 fra CDN). Ingen build-step nødvendig.

## Deploy til Vercel

### Alternativ 1: Vercel CLI (raskest)

```bash
cd visit-oslo-media
npx vercel
```

Følg promptene. Første gang ber den deg logge inn / koble prosjektet. Etterpå er det bare `npx vercel --prod` for å pushe nye versjoner.

### Alternativ 2: Drag & drop

1. Gå til https://vercel.com/new
2. Dra hele `visit-oslo-media`-mappen inn på siden
3. Trykk Deploy

### Alternativ 3: GitHub-integrasjon

1. Push mappen til et GitHub-repo
2. På vercel.com → Import Project → velg repo'et
3. Deploy (ingen build-konfig trengs — Vercel detekterer som static site)

## Konfigurasjon

Når dere skal koble på den ekte SuperOffice-backenden, åpne `index.html` og fyll inn `BACKEND`-objektet (rundt linje 580):

```js
const BACKEND = {
  baseUrl: 'https://onlineX.superoffice.com/CustXXXXX/CS/scripts/customer.fcgi',
  apiKey:  'din-api-nokkel',
  saveIncludeId: 'visit-oslo-save-mention',
  getIncludeId:  'visit-oslo-get-mention',
  listIncludeId: 'visit-oslo-list-mentions',
};
```

CRMScript-endepunktene som driver dette ligger i SuperOffice — se egen leveranse.

## Test modus

Toggle øverst til høyre. På som standard. Bruker dummy-forfattere og dummy-medlemmer, og lagrer i nettleserens localStorage så demoen overlever reload. Knappen «Tilbakestill data» gjenoppretter seed-eksemplene.

Slå av test modus for å snakke med ekte SuperOffice (krever konfig over).

## Filer

- `index.html` — hele appen
- `vercel.json` — clean URLs config
- `README.md` — denne filen
