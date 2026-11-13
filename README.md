# Boa

Klickbar prototyp av **Boa** – en personlig underhållsplan för villaägare. Appen visar ett årshjul med årets tolv månader, och för varje månad en checklista med underhållsuppgifter för huset (t.ex. rensa hängrännor, testa brandvarnare, se över ventilationen).

Prototypen är byggd som en enda statisk HTML-fil utan byggsteg eller beroenden, och visas som en mobilskärm i webbläsaren.

## Funktioner

- **Årshjul** – ett SVG-hjul med månads- och säsongsring. Välj en månad genom att klicka/trycka eller med piltangenterna.
- **Checklista per månad** – bocka av uppgifter, lägg till egna uppgifter och ta bort dem.
- **Sparat lokalt** – status sparas i webbläsarens `localStorage` (nyckel `boa-prototyp-v1`), så inget skickas till någon server.
- **Profil** – kontaktuppgifter, husinformation och inställningar för påminnelser (endast demo, inget sparas på riktigt).
- **Responsiv** – på desktop visas en telefonram när den får plats i full storlek; i mindre eller inzoomade fönster fyller appen fönstret i stället, så att zoom alltid förstorar texten.

## Kom igång

Inget behöver installeras.

1. Klona repot:
   ```bash
   git clone https://github.com/Twentytipsyone/Boa.git
   cd Boa
   ```
2. Öppna `index.html` direkt i webbläsaren, **eller** starta en lokal webbserver:
   ```bash
   python3 -m http.server 8000
   ```
   och gå till <http://localhost:8000>.

> Typsnittet Geist laddas från Google Fonts, så utan internet faller sidan tillbaka på systemtypsnittet.

### Återställ prototypen

Rensa sparad data genom att i webbläsarens konsol köra:

```js
localStorage.removeItem("boa-prototyp-v1"); location.reload();
```

## Filstruktur

| Fil | Beskrivning |
| --- | --- |
| `index.html` | Hela prototypen: markup, CSS och JavaScript |
| `images/house.png` | Hero-bild på startsidan |
| `images/house-blur.png` | Suddig bakgrundsbild på profilsidan |
| `images/avatar.png` | Profilbild |
| `CLAUDE.md` / `AGENTS.md` | Instruktioner för AI-kodagenter |

## Publicera

Eftersom allt är statiskt kan prototypen publiceras med t.ex. GitHub Pages (Settings → Pages → Deploy from branch → `main` / root). Observera att GitHub Pages för privata repon kräver ett betalt GitHub-konto.

## Status

Detta är en prototyp för att testa koncept och flöden. Kontoinställningar, utloggning och riktig lagring av profiluppgifter finns inte med.
