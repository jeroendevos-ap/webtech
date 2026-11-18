# Labo 7 - Typografie en kleur als systeem: vijf nabouw-opdrachten: modeloplossing

Dit is een mogelijke oplossing van labo 7, niet de enige. Vergelijk ze met je eigen werk: niet om over te nemen, maar om te zien waar jouw CSS afwijkt en of dat erg is. Een andere weg naar dezelfde screenshots is niet fout, zolang ze uit hoofdstuk 7 komt en elke waarde uit een token haalt; een weg die de regels breekt (een gewijzigde `index.html`, een letterlijke kleur of maat buiten het tokenblok, een link naar Google Fonts, een donkere query met meer dan tokens, id-selectors, `!important`) wel. De HTML-bestanden, `reset.css`, de lettertypes en de afbeeldingen zijn identiek aan de starter. De verwijzingen (7.6, F7.5) zijn naar de syllabus.

## 1. Tintenladder

Zie `tintenladder/css/stijl.css`. `body` is een grid met twee rijen (`auto 1fr`) en `min-height: 100svh`; `.ladder` is een grid met tien gelijke rijen. De hue staat één keer in `--hue`, en elke trede is één regel met `hsl(var(--hue) 55% L%)`; alleen de lightness verschilt. Vanaf de zesde trede zet `.trede:nth-child(n + 6)` de tekst in papier.

Reflectie: op de vijfde band (lightness 55%) haalt de inkt 4.7:1, op de zesde (45%) haalt het papier 4.67:1; allebei net boven de vloer van 4.5:1 (7.8). Leg je de wissel één band later, dan staat inkt op de zesde band en zakt de ratio naar zo'n 3.3:1: onder de vloer, en in de trein onleesbaar. Verander je `--hue` in 25, dan pas je één regel aan en kleurt de hele ladder terracotta: dezelfde hue, dezelfde verzadiging, tien keer dezelfde bewerking op de lightness, dat is het hele punt van hsl (7.6). Met hex-waarden had je tien kleuren opnieuw moeten uitzoeken.

Veelgemaakte fouten: de tien kleuren als hex of als tien losse hsl-waarden zonder `var(--hue)` (werkt, maar mist 7.6); de wissel naar papier per band herhaald in tien regels in plaats van één `:nth-child(n + 6)`; `height: 100vh` op de ladder in plaats van `min-height: 100svh` op `body` (F6.2, F3.10); de kop in een aparte box met vaste hoogte.

## 2. Leespagina

Zie `leespagina/css/stijl.css`. Vijf `@font-face`-regels, één per bestand: Fraunces gewoon en cursief met `font-weight: 100 900`, Atkinson Hyperlegible 400, 400 cursief en 700 (7.2). De browser kiest per element het juiste bestand op gewicht en stijl; `em` krijgt vanzelf de cursieve Atkinson, `strong` de vette. Het tokenblok bevat de schaal (ratio 1.25), de vijf spacing-treden en de vijf kleurrollen; verderop staat geen enkele letterlijke waarde meer. De kolom is `max-width: 65ch` met `margin: 0 auto` (7.3). Elke kop heeft haar eigen regelhoogte (F7.3), en de witruimte volgt de vuistregel van 7.5: een h2 heeft xl boven zich en s onder zich.

Reflectie: `ch` is de breedte van het cijfer 0 in de actieve letter, en in Atkinson Hyperlegible op 16px is die zo'n 10.4px, geen 16px; 65ch is dus zo'n 674px (7.3). Kies je een smallere letter, dan wordt de kolom smaller, en wie inzoomt, houdt dezelfde regellengte in tekens. Zet je de ratio op 1.2, dan worden de koppen bescheidener (xxxl wordt 2.074rem in plaats van 2.441rem) en de intro kleiner; je past zes tokens aan en verder niets (7.4). Het aantal verschillende waarden voor `margin` en `padding` hoort precies de vijf spacing-tokens te zijn, plus `0` en `auto` (F7.5).

Veelgemaakte fouten: één `@font-face` voor Fraunces zonder `font-style: italic` voor het tweede bestand, waardoor de browser het citaat zelf scheef trekt (faux italic); het pad `fonts/...` in plaats van `../fonts/...` (het pad vertrekt vanuit `css/`, 1.9; het Network-paneel toont de 404); `max-width: 40rem` in plaats van 65ch (werkt, maar meet ruimte in plaats van leesbaarheid); koppen zonder eigen regelhoogte (F7.3); marges als losse rem-waarden naast de schaal (F7.5); kapitalen getypt in plaats van `text-transform` (7.3).

## 3. Frituur 't Pleintje

Zie `frituur/css/stijl.css`. `:root` krijgt `color-scheme: light dark` en de vijf rollen in hsl; de donkere query herdefinieert diezelfde vijf en verder niets (7.9). `body` is een grid van drie rijen met `min-height: 100svh`, zodat de voet onderaan blijft (4.7); `main` is een zelforganiserend raster (6.8) waarin het kader met `grid-column: 1 / -1` over alle kolommen loopt (4.6). Elke menuregel is een flex-rij met `justify-content: space-between`. De labels gebruiken het accent als achtergrond en het oppervlak als tekst: in het donker wordt het oppervlak donker en het accent licht, en het label klopt vanzelf.

Reflectie: de donkere query telt vijf declaraties. Staan er meer, dan schreef je ergens een kleur buiten het tokenblok (F7.8), typisch een `white` op het label of een `#fff` op de voet. Het label "nieuw" haalt 4.6:1 in het licht en 8.6:1 in het donker; de lichte versie is de krapste, en net goed genoeg. De tekst van het label staat in `--color-surface` omdat `white` in het donker wit blijft, op een accent dat dan licht is: twee kleuren die elkaar niet meer kennen. Een rol volgt het schema, een letterlijke kleur niet (7.7).

Veelgemaakte fouten: een tweede stylesheet in de donkere query (F7.9); `color: white` op het label (F7.8); `color-scheme` vergeten, waardoor de schuifbalk licht blijft; de prijs met een vaste breedte in plaats van `justify-content: space-between`; `height: 100vh` op `body` (F6.2); het kader niet over de kolommen (werkt, maar wijkt af van het screenshot).

## 4. De kaaien

Zie `kaaien/css/stijl.css`. De held krijgt de foto met de vier background-properties apart (7.10): `cover`, `center`, `no-repeat`, en `min-height: 70svh`; als grid met `align-items: end` zet hij het vlak onderaan (4.7). Het vlak heeft `rgb(0 0 0 / 0.55)` als achtergrond: dat is de contrastmaatregel voor tekst op een foto (F7.10). Het kader krijgt het kompas één keer, rechtsonder, 8rem breed, met `background-position: right 1rem bottom 1rem`; de voet krijgt de golfjes zonder `background-repeat`, dus met de standaardwaarde `repeat`, en zet de tekst op een vlak in de oppervlaktekleur zodat ze niet op het patroon zelf staat.

Reflectie: de foto is sfeer, geen inhoud; wie ze niet ziet, mist niets van wat de pagina zegt, dus hoort ze niet in een `img` met alt-tekst maar in de CSS (7.10). Zonder het donkere vlak staat de witte titel op het lichtste deel van de foto, de lucht, op een ratio van zo'n 1.25:1 (F7.10); met het vlak haalt het lichtste punt onder de titel zo'n 5.6:1 en het donkerste bijna 15:1. Het vlak is wat de titel leesbaar maakt, niet de foto. `no-repeat` op de voet laat één tegel van 96 bij 48 px over in de linkerbovenhoek; `contain` op de held toont de hele foto met lege banden ernaast of erboven, in plaats van de box te vullen.

Veelgemaakte fouten: de foto als `img` met de tekst erover gepositioneerd (werkt, maar is het verkeerde gereedschap voor decor, en vraagt om `position`); tekst rechtstreeks op de foto (F7.10); `background-size: contain` of geen `background-size`, waardoor de foto op 1600px herhaalt; het kompas met `background-position: right bottom` tegen de rand; de golfjes met `no-repeat`; `height` in plaats van `min-height` op de held (F3.10).

## 5. Fietsatelier Noord

Zie `fietsatelier/css/stijl.css` en `fietsatelier/css/thema.css`. In `stijl.css` staat alles wat de site is: layout, maten, en elke kleur, letter en hoek via `var()`. De tokens voor A staan in `:root`. `thema.css` bevat drie `@font-face`-regels en één `:root`-blok met acht tokens voor B; omdat het later gelinkt is, winnen die waarden op volgorde (2.7). Screenshot A is de pagina met een lege `thema.css`, screenshot B dezelfde pagina met `thema.css` ingevuld; `stijl.css` is tussen beide niet aangeraakt.

Reflectie: als er in `stijl.css` nog een letterlijke kleur, letter of maat buiten `:root` staat, zie je dat in screenshot B meteen: dat ene element verandert niet mee (F7.8). De klassiekers zijn `transparent` of `white` op een hover, een `Georgia` die in een selector bleef staan, en een `border-radius` die niet via `--radius` loopt. `thema.css` telt zonder de `@font-face`-blokken acht regels, en dat is de les voor B7.1: een site met een echt systeem herstijl je door één blok te herschrijven. Vergt het meer, dan is er geen systeem.

Veelgemaakte fouten: de hoeken als letterlijke `1rem` in `stijl.css` in plaats van `var(--radius)`, waardoor A ronde hoeken krijgt of B geen; de `@font-face`-regels in `stijl.css` in plaats van in `thema.css` (werkt, maar dan laadt A letters die ze niet gebruikt); de kleuren van de knop bij hover letterlijk geschreven (F7.8); `thema.css` met meer dan tokens, bijvoorbeeld een nieuwe regel voor de knop (dan is het geen tokenwissel meer maar een tweede stylesheet, F7.9); de prijs niet onderaan de kaart (geen `margin-top: auto` in een flex-kolom, 5.3).

## Thuis: B7.1

Geen modeloplossing: je site is van jou. Waar je zelf op controleert: zelfgehoste letters in `site/fonts/` met `@font-face` en een licentiebestand; een typografische schaal en een spacing-schaal als tokens, en geen enkele losse waarde erbuiten (de telling van de Klaar?-stap is nul); vijf kleurrollen in hsl, elk paar gemeten op minstens 4.5:1; een donkere query met niets anders dan tokens; en de tokenwissel als bewijs, met twee screenshots in `site/review/`.
