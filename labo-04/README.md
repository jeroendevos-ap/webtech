# Labo 4 - reflecties

Naam: Jeroen De Vos (modeloplossing)

## 1. Drie kolommen

- `display: flex` staat op `main`, de container. `flex` staat op de drie `div`s, de items: `flex: 1` op de buitenste, `flex: 2` op de middelste. De kolommen zijn daarnaast zelf flex-container (met `justify-content` en `align-items: center`) om hun cijfer te centreren.
- `display` bepaalt hoe een element zijn **kinderen** schikt; `flex` bepaalt hoe een **item** zich gedraagt binnen de container van zijn ouder (groeien, krimpen, basisbreedte). Het zijn twee rollen op twee niveaus: `flex` op `main` zou niets doen, want `body` is geen flex-container (4.1, F4.2).

## 2. Navigatiebalk

- `justify-content` verdeelt de ruimte langs de hoofdas (hier horizontaal: `space-between` duwt naam en navigatie uit elkaar); `align-items` lijnt uit op de kruisas (hier verticaal: `center`) (4.3).
- Met `margin-right` op elke `li` krijgt ook de laatste link een marge: het blok links schuift `0.5rem` van de rechterrand weg en staat niet meer op de `2rem` padding van de balk. Je zou het met `:last-child` moeten wegwerken; `gap` zet ruimte alleen *tussen* items (F4.7).

## 3. Mondriaan

- Het zijn er eigenlijk **drie**: `.lila` en `.olijf` (brede vlakken, `grid-column: 1 / 4`) en `.marine` (`grid-column: 4`). Zonder die laatste zet de auto-placement marine meteen naast geel, in kolom 2 van rij 2: de lege cellen moeten *vóór* marine komen, en de impliciete vulling slaat nooit uit zichzelf cellen over. Bruin, geel en rood landen vanzelf goed: na de brede lila is in rij 1 alleen kolom 4 vrij (bruin), geel neemt de eerste vrije cel van rij 2, en na de brede olijf in rij 3 blijft enkel kolom 4 over voor rood (4.5, 4.6).
- Met `gap` en padding op de container is elke lijn exact even dik (`2vh`), ook aan de buitenrand, en het blauw schijnt automatisch door in de lege cellen. Met een border op elk vlak zouden twee aangrenzende vlakken een dubbel dikke lijn geven, zou de border de inhoud van het vlak eten, en bleven de lege cellen wit in plaats van blauw.

## 4. Trap

- Zonder `grid-row` staan alle vier de treden op de eerste rij, naast elkaar (elk 320 x 200). Met enkel een kolom en een `auto` rij zoekt de auto-placement in de huidige rij de eerste plek vanaf die kolom; kolom 1, 2, 3 en 4 zijn in rij 1 allemaal vrij, dus de cursor springt nooit naar een volgende rij. Rijen 2 tot 4 blijven leeg maar bestaan wel (expliciete grid van vier rijen) (4.5).
- `grid-column: 4 / -1` betekent: van kolomlijn 4 tot de laatste lijn van de expliciete grid. Een raster van vier kolommen heeft vijf lijnen, en `-1` is lijn 5, dus het is hetzelfde als `4 / 5` of gewoon `4`. Negatieve lijnnummers tellen alleen in de expliciete grid; hier is die er (`repeat(4, 1fr)`), dus het werkt.

## 5. Dierenasiel Zonnehoek

- Zes layoutcontainers:

  | Container | Gereedschap | Waarom |
  |---|---|---|
  | `body` | grid, `auto 1fr auto` | grondplan: header, main, footer onderaan (sticky footer) |
  | `header` | flex | één as: naam links, navigatie rechts |
  | `nav ul` | flex | één as: rij links met `gap` |
  | `main` | grid, één kolom | leeskolom: kop, intro en rooster onder elkaar met `gap` |
  | `.kaarten` | grid, drie kolommen | twee assen: rooster, `.uitgelicht` van lijn 1 tot 3 |
  | `.kaart` (x5) | flex, `column` | één as: `.beschrijving` krijgt `flex: 1`, knop zakt naar onder |

- Op 640 px breed blijven er drie kolommen van ongeveer 170 px: de kaarten worden smalle kokers waarin de tekst per twee woorden afbreekt, en de navigatie loopt bijna tegen de naam. Het rooster past zich niet aan de breedte aan. Dat lossen we op met media queries en responsive grids (`repeat(auto-fit, minmax(...))`) in hoofdstuk 5.

## Thuis: B4.1 (met AI of zonder AI)

Welke route koos je? Bij de AI-route: prompt en onbewerkte output staan in `site/review/`, en dit corrigeerde ik (met verwijzing naar de sectie of het foutnummer):

1. 
2. 
3. 
