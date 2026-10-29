# Labo 6 - Het onbekende scherm: vijf nabouw-opdrachten, nu responsive: modeloplossing

Dit is een mogelijke oplossing van labo 6, niet de enige. Vergelijk ze met je eigen werk: niet om over te nemen, maar om te zien waar jouw CSS afwijkt en of dat erg is. Een andere weg naar dezelfde screenshots is niet fout, zolang ze mobile-first is en uit hoofdstuk 4 tot 6 komt; een weg die de regels breekt (een gewijzigde `index.html`, queries boven de basis, `max-width`-queries door elkaar met `min-width`, breekpunten in px, een horizontale schuifbalk op een smal scherm, id-selectors, `!important`) wel. De HTML-bestanden en `reset.css` zijn identiek aan de starter. De verwijzingen (6.4, F6.4) zijn naar de syllabus.

## 1. Kleurvlakken

Zie `kleurvlakken/css/stijl.css`. `main` is een grid met `min-height: 100svh` en in de basis geen kolommen: vier items, vier impliciete rijen van `1fr`, dus vier even hoge banden. Vanaf 37.5rem krijgt het `repeat(4, 1fr)` kolommen (één rij, vier kolommen); vanaf 50rem `repeat(2, 1fr)` kolommen én `repeat(2, 1fr)` rijen. Elke query bevat alleen wat verandert.

Reflectie: verwissel je de queries, dan staat de 50rem-query vóór de 37.5rem-query; op 1280 px matchen ze allebei, en de laatste wint (volgorde, 2.7): vier kolommen in plaats van twee bij twee. Een query voegt geen specificiteit toe (6.4, F6.4), dus de volgorde beslist. `100svh` is de kleinste viewport op mobiel, mét browserbalken in beeld; `100vh` is de grootste en loopt op een telefoon net achter de balk (F6.2).

Veelgemaakte fouten: de queries met `max-width` geschreven vanaf de brede versie (F6.5); breekpunten in px (F6.6); de kleuren in elke query herhaald (F6.8); `height: 100vh` op de vlakken zelf in plaats van `min-height` op de container (F3.10).

## 2. Dashboard

Zie `dashboard/css/stijl.css`. De basis is een grid met `gap` en één kolom; de tegels hebben `min-height: 6rem` en vallen onder elkaar in de volgorde van de HTML, zonder één plaatsingsregel. Vanaf 50rem: twee kolommen, en de titel, de grafiek en het weer krijgen `grid-column: 1 / -1` (van de eerste lijn tot de laatste); de vier kleine tegels plaatst de browser zelf, in volgorde, twee per rij. Vanaf 75rem: vier kolommen, `auto 1fr 1fr` als rijen (de vierde rij ontstaat vanzelf), de grafiek op `grid-column: 1 / 3` en `grid-row: 2 / 4`, elke kleine tegel op haar eigen kolom en rij (omzet en agenda op rij 2, bezoekers en taken op rij 3), en `min-height: 100svh` op het dashboard. De titel en het weer houden hun `1 / -1` uit de vorige query.

Reflectie: `grid-column: 1 / -1` in de basis is onschuldig maar zinloos: op één kolom is lijn 1 tot -1 gewoon die ene kolom. Wat pas vanaf 50rem iets betekent, hoort in die query (6.3). In de query van 75rem herhaal je het niet: de query van 50rem matcht óók op 1280 px, dus de titel en het weer spannen nog altijd alle kolommen; alleen wat verandert staat erbij, en voor de grafiek is dat een nieuwe kolom- én rijspanne die de vorige overschrijft (F6.8, het hele mobile-first-contract). `-1` is de laatste lijn van het expliciete raster, hoeveel kolommen er ook zijn (4.6, motorkap hoofdstuk 4). Vergeet je bij de grafiek `grid-row: 2 / 4`, dan neemt ze één rij hoog, en schuiven bezoekers en taken niet mee: ze staan op rij 3 naast een lege plek; de grid-overlay in DevTools toont het meteen.

Veelgemaakte fouten: de kleine tegels ook in de query van 50rem geplaatst (werkt, maar is overbodig: de browser vult in volgorde); `grid-column: 1 / 2` voor de grafiek op 75rem in plaats van `1 / 3` (één kolom breed); `span 2` zonder begin (werkt, maar dan hangt de plek af van de volgorde); `min-height: 100svh` in de basis, waardoor zeven tegels op een telefoon uitgerekt worden; de plaatsing herhaald in de tweede query (F6.8).

## 3. Scheldekaai Festival

Zie `festival/css/stijl.css`. De header is in de basis een flex-container in richting column met `align-items: center`; de `ul` is een flex-kolom met `width: 100%`, en elke link is `display: block` met padding, rand en ronde hoeken: een knop over de volle breedte (3.7). Vanaf 50rem draait de `ul` naar `row` met `justify-content: center` en verliest ze haar breedte; vanaf 75rem draait de header zelf naar `row` en krijgt het logo `margin-right: auto` (5.3). De held, de h1 en het programma staan in `clamp()` (6.7). In elke programmaregel is de locatie met `margin-left: auto` naar rechts geduwd.

Reflectie: `5vw + 1rem` is op 400 px 20 + 16 = 36px, boven de ondergrens van 32px, dus 36px; op 800 px 40 + 16 = 56px; op 1280 px 64 + 16 = 80px, boven de bovengrens van 64px, dus 64px. De rem-term zorgt dat de titel meegroeit als een gebruiker inzoomt of zijn lettergrootte verhoogt; pure vw doet dat niet (F6.7). Twee breekpunten omdat er twee dingen breken op een andere breedte: vier knoppen passen op één rij vanaf zo'n 800 px, maar logo én knoppen naast elkaar pas vanaf zo'n 1200 px; breekpunten leg je waar het ontwerp breekt (6.4).

Veelgemaakte fouten: `width: 100%` op de `ul` in de query vergeten terug te zetten, waardoor de rij knoppen niet centreert; de h1 in vw zonder grenzen (F6.7); de query herhaalt de kleuren, randen en padding van de knoppen (F6.8); `margin-right: auto` op het logo in de basis, waar het in een kolom niets doet; hover zonder focus (F2.11).

## 4. Tribune

Zie `tribune/css/stijl.css`. De basis is een grid zonder kolommen met `min-height: 100svh`, `gap` en padding: tien banden. Vanaf 62.5rem: `repeat(10, 1fr)` kolommen, en rij n krijgt `grid-column: n / -1`. Elke rij begint één lijn verder en loopt tot de laatste lijn (4.6, motorkap hoofdstuk 4).

Reflectie: de impliciete grid plaatst elk volgend item op de volgende rij zodra de vorige rij vol is; omdat elke rij tot `-1` loopt, is elke rij meteen vol, en volgt `grid-row` vanzelf (4.5). `auto-fit` met `minmax()` maakt zoveel gelijke kolommen als er passen (6.8), maar kan een item niet op een vaste lijn zetten; de tribune is een plaatsingsvraag, geen vraag over hoeveel kolommen er passen. Het verkeerde gereedschap dus.

Veelgemaakte fouten: `grid-column: n / 11` in plaats van `n / -1` (werkt, maar breekt als het raster van maat verandert); de tien kolommen in de basis zetten, waardoor de banden op een telefoon in een rij van tien smalle strookjes staan; `height` op de rijen.

## 5. Affiche

Zie `affiche/css/stijl.css`. De affiche krijgt `width: min(28rem, 100% - 2rem)` en `aspect-ratio: 3 / 4`: op een breed scherm 28rem, op een smal scherm de volle breedte min 1rem aan elke kant, dus nooit een schuifbalk (6.6), en de hoogte volgt uit de verhouding (5.6). Ze is `position: relative` (het anker) en een flex-kolom met `justify-content: center`, zodat de tekst in het midden staat en de hoeken vrij blijven. De maat van de stickers staat in één custom property, `clamp(4rem, 14vw, 7rem)`; elke sticker is `display: grid` met `place-items: center`. In de basis liggen de vier stickers schuin over de linkerbovenhoek, telkens 1.5rem verder; prijs en uitverkocht staan in de HTML vóór de sticker waar ze op moeten liggen en krijgen daarom `z-index: 1` (5.5). Vanaf 50rem verhuizen logo en uitverkocht naar rechtsonder: `top` en `left` op `auto`, `bottom` en `right` gezet. Vanaf 62.5rem verhuist de prijs naar rechtsboven en het logo naar linksonder, en uitverkocht naar de hoek.

Reflectie: `width: 28rem` is een maat, geen grens; op 400 px is 28rem 448px, en de box steekt buiten het venster: de horizontale schuifbalk (F6.3). In DevTools maak je het venster smal en klim je door de Elements-boom tot het element waarvan de highlight breder is dan de pagina. `top: auto` haalt de waarde uit de basis weg; laat je het weg, dan gelden `top` én `bottom` tegelijk, en de sticker wordt uitgerekt tussen beide.

Veelgemaakte fouten: de affiche met `height` in plaats van `aspect-ratio` (F3.10); de stickers in px of een vaste rem, waardoor ze op 400 px de halve affiche bedekken; `top: auto` vergeten in de query (de sticker rekt uit); de z-index vergeten, waardoor de datum op de prijs ligt; de tekst onderaan de affiche, waar de stickers hem vanaf 800px bedekken.

## Thuis: B6.1

Geen modeloplossing: je site is van jou. Waar je zelf op controleert: mobile-first met alle queries onder de basis en in rem; de kantelende plattegrond, met `grid-column` en `grid-row` in de query (6.3) of met `grid-template-areas` zoals in labo 5; een kaartenrooster met `repeat(auto-fit, minmax())`; `clamp()` op minstens de h1; decoratieve hover in `(hover: hover)`; `loading="lazy"` onder de vouw; geen horizontale schuifbalk tussen 320 px en 1280 px; en één echt toestel in je README.
