# Labo 5 - reflecties

Naam: Jeroen De Vos (modeloplossing)

## 1. Letterraster

- Een gebied moet een rechthoek zijn. Zet je "a" in een L-vorm (bv. `"a a . b" "a d e f" "g . . h"`), dan is de hele `grid-template-areas` ongeldig en gooit de browser de declaratie weg: er bestaat dan geen enkel gebied meer. Elke `grid-area: a`, `b`, ... verwijst naar een naam die niet bestaat; de browser maakt impliciete lijnen `a-start`/`a-end` *ná* het expliciete raster, en alle acht vlakken stapelen zich op in één piepkleine impliciete cel rechtsonder (F5.6). In DevTools zie je de declaratie doorstreept met een waarschuwingsteken. (Zet je "a" in dezelfde kolom op rij 2, `"a . . b" "a d e f"`, dan is dat wél een geldige rechthoek: a wordt dubbel zo hoog, en c verliest zijn gebied en belandt in een impliciete cel.)
- Met lijnnummers kost elk vlak twee declaraties (`grid-column` en `grid-row`), dus 16 declaraties voor 8 vlakken; met areas zijn het er 9: één `grid-template-areas` en één `grid-area` per vlak, en het raster staat leesbaar als tekening in de CSS. (Strikt genomen volstaat bij lijnnummers ook `grid-area: 1 / 1`, maar dat leest niemand meer terug.)

## 2. Citaten

- Flexbox is één as per rij: elke rij is een eigen flex-lijn, en de items van rij 2 weten niets van de breedtes in rij 1. Groei en krimp worden per rij verdeeld. Grid tekent kolommen over de twee assen, zodat alle rijen dezelfde kolomlijnen delen (5.2, 4.2). Hier toevallig gelijk omdat beide rijen vier items tellen; met zeven citaten zouden de drie van rij 2 elk een derde van de breedte innemen.
- Bij een basis van 30rem (480 px) passen er bij 1280 px nog maar twee naast elkaar: 3 x 30rem plus twee gaps is breder dan de 1232 px beschikbare ruimte, dus breekt de rij na twee, en groeien die twee elk tot de halve breedte. Vier rijen van twee in plaats van twee rijen van vier: de basis bepaalt hoeveel er op een rij passen, `grow` verdeelt daarna de rest.

## 3. Fotolijst

- Zonder `position: relative` op `.lijst` is er geen gepositioneerde voorouder meer: het anker wordt het initial containing block, ongeveer het venster. Groen en roze landen op 2rem en 5rem van de linkerbovenhoek van de *pagina*, lime en rood op 6rem en 3rem van de rechteronderhoek van het *venster*, ver buiten de foto (F5.1).
- Zonder `z-index` volgen gepositioneerde elementen de bronvolgorde: wie later in de HTML staat, wordt later geschilderd en ligt bovenop. Roze staat in `index.html` vóór groen, dus groen ligt erover, ook al staat roze verder naar rechts en onder. Positie op het scherm zegt niets over de stapelvolgorde. Met `z-index: 1` en `2` (op groen/roze en lime/rood) beslis je het zelf, met kleine getallen.

## 4. Toonzaal

- Zonder `top: 0` heeft sticky geen drempel: er is geen offset waarop het element moet blijven plakken, dus gedraagt de header zich als `position: relative` en scrolt hij gewoon mee weg (F5.2).
- `sticky` houdt de header in de flow: hij neemt zijn 3.5rem in, en de inhoud begint eronder. `fixed` haalt hem uit de flow: de rest van de pagina schuift omhoog en de h1 verdwijnt achter de balk. Fixed zou dus een extra `padding-top: 3.5rem` op `body` (of `main`) nodig hebben om het gat op te vullen, en die waarde moet je dan in sync houden met de hoogte van de balk (5.4). Bij beide blijft `scroll-padding-top` op `html` nodig voor de interne links.

## 5. Koffiebar Kaai 12

- De drie vragen:

  | Vraag | Waar | Gereedschap |
  |---|---|---|
  | Container | `body` (named areas: kop, zij, inhoud, voet), `header` en `nav ul` (flex-rij), `main` (grid), `.kaarten` (grid van 3 kolommen), `.kaart` en `.tekst` (flex-column) | grid en flexbox |
  | Item | `.logo` (`margin-right: auto`), `.tekst` (`flex: 1`), `.prijs` (`margin-top: auto`), de foto (`width`, `aspect-ratio`, `object-fit`), `:has(img)` / `:not(:has(img))` | item-eigenschappen en `:has()` |
  | Plaatsing | `.badge` (`position: absolute` tegen `.kaart` met `position: relative`) | positioning, enkel voor wat óp de kaart ligt |

- Zonder `aspect-ratio` krijgt elke foto zijn eigen verhouding op 304 px breed: espresso (2:3) wordt 456 px hoog, cappuccino 304, taart 203, croissant 114. Elke rij rekt mee tot de hoogste kaart (`align-items: stretch` in grid, F4.5): rij 1 groeit van 441 naar 643 px, en de koppen en teksten staan in elke kaart op een andere hoogte. Het rooster blijft dicht, maar oogt rommelig; de vaste verhouding is wat de kaarten gelijk maakt (F5.9).

## Thuis: B5.1 (met AI of zonder AI)

Welke route koos je? Bij de AI-route: prompt en onbewerkte output staan in `site/review/`, en dit corrigeerde ik (met verwijzing naar de sectie of het foutnummer):

1. 
2. 
3. 
