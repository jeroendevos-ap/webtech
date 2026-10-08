# Labo 3 - reflecties

Naam: Jeroen De Vos (modeloplossing)

## 1. Kleurenstalen

- Welke twee waarden uit de user agent stylesheet moest je op de lijst wegwerken, en waar las je ze af?
  `padding-left: 40px` (de insprong) en `list-style-type: disc` (de bolletjes). De padding lees je af in het boxmodel-diagram van de `ul` in het Computed-tabblad (40 aan de linkerkant van de padding-ring); de bolletjes staan als `list-style-type` in de Styles-pane onder *user agent stylesheet*. Daar zie je ook `margin-block: 1em`: die zet de reset niet op nul (lijsten staan niet in regel 2), dus zonder `margin: 0` werd de pagina 2rem hoger dan het screenshot (2032 px in plaats van 2000 px).
- Wat verandert er aan de banden als je het venster hoger maakt, en wat verandert er niet?
  Hoger venster: elke band wordt mee hoger, want `height: 50vh` is altijd de helft van de vensterhoogte, en de pagina blijft precies 2,5 vensters hoog. Wat niet verandert: de tekstgrootte, de letterafstand en de afstand van de tekst tot de bovenrand van de band (`padding-top: 11rem`), want die staan in rem en hangen niet af van het venster.

## 2. Slogan

- Welke property centreerde de tekst, en welke de kolom?
  De tekst: `text-align: center` (op `body`, en het erft door naar h2, p en de knop). De kolom: `width: 40rem` met `max-width: 100%` plus `margin: 12rem auto 0`; de twee auto-marges verdelen de vrije ruimte links en rechts gelijk.
- Waarom werkte de padding op de knop pas na `display: inline-block`?
  Een `a` is inline. Bij een inline box tekent de browser de padding wel, maar die duwt de regel niet open: verticale padding en `margin-top` tellen niet mee voor de lijnhoogte, dus de knop overlapt de paragraaf erboven. Met `inline-block` wordt de knop een echte box met volledig boxmodel (padding en marge duwen de omgeving weg), en omdat hij nog in de tekstregel staat, centreert `text-align` hem. Met `display: block` zou hij over de volle 40rem uitrekken.

## 3. Tabblad

- Wat is de visuele breedte van het tabblad, en waarom is dat exact 15rem en geen 15rem plus padding plus border?
  15rem = 240 px. De reset zet `box-sizing: border-box` op elk element (regel 1), dus `width` meet tot en met de border: 240 = 4 (border) + 32 (padding) + 168 (content) + 32 + 4. Het boxmodel-diagram toont daarom een content-breedte van 168. Met de standaard `content-box` zou het tabblad 240 + 64 + 8 = 312 px breed zijn. De schaduw telt niet mee: `box-shadow` neemt geen ruimte in.

## 4. Donut

- Waarom werkt `height: 70%` op de cirkel, terwijl F3.2 zegt dat een procentuele hoogte meestal niets doet?
  Een procentuele hoogte rekent tegen de hoogte van de ouder, en meestal heeft de ouder geen expliciete hoogte (hij is zo hoog als zijn inhoud), dus valt `height: %` terug op `auto`. Hier heeft `main` wél een expliciete hoogte (`height: 90vh`), dus 70% van de content-hoogte van main (720 − 2 × 12 = 696 px) geeft 487 px. Hetzelfde geldt een niveau dieper: de cirkel heeft nu een vaste hoogte, dus `height: 90%` op de h1 werkt ook.
- Tegen welke maat van de ouder rekende de browser `margin: 15%`: de breedte of de hoogte?
  De breedte, ook voor `margin-top` en `margin-bottom`: procentuele marges en padding rekenen altijd tegen de breedte van het containing block. Computed: 104,4 px = 15% van 696. Hier valt dat niet op omdat main vierkant is; maak je main breder dan hoog, dan worden de boven- en ondermarge ook groter. Hetzelfde verklaart `padding-top: 40%` op de h1: 40% van de breedte van de cirkel.

## 5. Landingspagina

- Gaf je `main` een `height` of een `min-height`, en waarom?
  `min-height: 80vh`. Een `height` is een plafond: is het venster laag of smal, dan wordt de inhoud (tekst en afbeelding) hoger dan 80vh en loopt hij uit de blauwe hero (overflow). `min-height` is een vloer: de hero is minstens 80% van het venster, en groeit mee als de inhoud meer ruimte vraagt.
- Wat gebeurt er met de twee helften als je een regeleinde zet tussen `</article>` en `<div class="afbeelding">`?
  Inline-blocks staan in een tekstregel, en witruimte tussen twee inline elementen wordt één spatie (ongeveer 4 px bij 16 px Arial). 50% + spatie + 50% is meer dan 100%, dus de afbeelding past niet meer naast de tekst en springt naar een nieuwe regel, onder het artikel. Zonder witruimte tussen de tags is er geen spatie en passen ze precies.

## Thuis: B3.1 (met AI of zonder AI)

Welke route koos je? Bij de AI-route: prompt en onbewerkte output staan in `site/review/`, en dit corrigeerde ik (met verwijzing naar de sectie of het foutnummer):

1. 
2. 
3. 
