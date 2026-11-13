# CLAUDE.md

Instruktioner för AI-kodagenter som arbetar i det här repot.

## Projektet

Boa är en klickbar prototyp av en personlig underhållsplan för villaägare. Kärnan är ett årshjul (12 månader + 4 säsonger) där varje månad har en checklista med underhållsuppgifter. Gränssnittet och all text är på **svenska**.

## Teknik

- En enda fil: `index.html` med inbäddad CSS (`<style>`) och JavaScript (`<script>`, en IIFE).
- Ren HTML/CSS/vanilla JS. Inga ramverk, inget byggsteg, ingen `package.json`.
- Typsnitt: Geist via Google Fonts, med fallback till systemtypsnitt.
- Data sparas i `localStorage` under nyckeln `boa-prototyp-v1`. Ingen backend.
- Bilder (`house.png`, `house-blur.png`, `avatar.png`) ligger i roten och refereras relativt.

## Köra lokalt

```bash
python3 -m http.server 8000
# öppna http://localhost:8000
```

Det går också att öppna `index.html` direkt i webbläsaren.

## Struktur i index.html

- **CSS-variabler** i `:root` (`--ink`, `--primary`, `--accent`, `--danger` m.fl.). Använd dem i stället för hårdkodade färger.
- **Skärmar**: `<main class="screen">` med id `screen-arshjul` (startsida) och `screen-profil`. Klassen `active` visar en skärm; flikraden (`.tabbar`, `data-target`) växlar mellan dem.
- **Konstanter i JS**: `MONTHS`, `SHORT`, `SEASON`, `MONTH_SEASON`, `DEFAULT_ITEMS` (två standarduppgifter per månad).
- **State**: `{ month, items[12][] }` där varje uppgift är `{ id, text, done, custom }`. Ändra state och anropa sedan `commit()` (sparar, ritar om checklistan och uppdaterar hjulet).
- **Viktiga funktioner**: `sector()` (SVG-geometri), `updateWheel()`, `renderChecklist()`, `selectMonth()`, `toast()`, `fit()` (skalar telefonramen på desktop).

## Riktlinjer

- Behåll upplägget med en fil och inga beroenden om inte användaren ber om något annat.
- Skriv all UI-text på svenska.
- Bevara tillgängligheten: `aria`-attribut, tangentbordsnavigering i årshjulet (Enter/Space/piltangenter) och synliga fokusmarkeringar.
- Om strukturen i `state` ändras, byt versionen i `STORE_KEY` så att gammal sparad data inte orsakar fel.
- Testa både desktopvyn (telefonram) och mobilvyn (≤ 520 px).

## Säkerhet och integritet

- Committa aldrig API-nycklar, tokens, lösenord eller `.env`-filer.
- Använd påhittade exempeldata i prototypen, aldrig riktiga personuppgifter.
