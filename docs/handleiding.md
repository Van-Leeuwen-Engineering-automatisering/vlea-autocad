# Handleiding – VLEA, kaarten voor AutoCAD

> **Versie 0.2.5.** Voor AutoCAD 2025, 2026 en 2027. `VKHELP` opent deze pagina in je browser.

## 1. Voordat je begint
- AutoCAD 2025, 2026 of 2027 voor Windows (ook Civil 3D of Map 3D). Niet AutoCAD LT, AutoCAD voor Mac of AutoCAD Web: die kunnen deze plugin niet laden (AutoCAD
  LT laadt geen .NET-plugins).
- Installeren: download `VLEA-AutoCAD-Setup.exe` bij de nieuwste release, sluit AutoCAD, open het
  bestand en klik op **Installeren**. Verwijderen kan met hetzelfde programma. Alle stappen, ook die met
  de zip en `Installeer.bat`, en wat je doet als Windows waarschuwt: zie de
  [README](../README.md#installeren).
- Je tekening staat in **meters, in RD** (Rijksdriehoekscoördinaten). Staat `INSUNITS` op een andere
  eenheid, dan weigert VLEA te tekenen en legt uit waarom; in het palet staan de kaarten dan grijs, met
  de reden erboven. Staat hij op 0 ("geen eenheid"), dan waarschuwt VLEA één keer.
- **Let op bij een nieuwe tekening:** een tekening uit het metrische standaardsjabloon staat in
  millimeters (`INSUNITS` 4). Zet de eenheid op meters: typ `UNITS` en kies bij **Insertion scale** (invoegschaal)
  "Meters" (of typ `INSUNITS` en dan `6`). Teken je zelf al in millimeters, dan passen RD-meters er
  niet bij: begin dan met een tekening in meters.
- Sla je tekening op voordat je een luchtfoto, de BRT (standaard een plaatje) of het kaartbeeld van de BGT laadt: het beeld komt in een map naast de tekening.

## 2. Het palet
Na de installatie opent het palet één keer vanzelf. Daarna: typ `VKPALET` of klik op het
lint-tabblad **VLEA** op **Palet** (nog een keer = sluiten). Van boven naar beneden:

- **Kop** (oranje): de link **vanleeuwenea.nl** opent de website van VLEA en **?** opent deze
  handleiding, allebei in je browser en zonder het commando af te breken waar je mee bezig bent (de
  versie en de mappen toont `VKHELP` op de opdrachtregel). Het **tandwiel** opent de instellingen (zie
  hieronder).
- **Gebied** – kies waar de kaart moet komen (zie 3): een adres zoeken, of de knoppen **Rechthoek**,
  **Polylijn** en **Contour** (een strook langs een lijn, met de breedte uit de instellingen).
  Daaronder staat het gekozen gebied.
- **Kaarten** – per soort een groep (ondergrond, hoogte, grondonderzoek, infra, natuur, beperkingen).
  Elke kaart heeft een eigen knop **Laden**: die laadt alleen die kaart, in het gekozen gebied, met de
  opties uit de instellingen. Er is niets om vooraf aan te vinken. Een kaart die nu niet kan, staat
  grijs met de reden eronder: "te groot (max. … km²)" (de uitleg bij de knop zegt wat de kaart zou
  ophalen, zie 4), "alleen Civil 3D", of "niets gekozen in de instellingen" (alle onderdelen van die
  kaart staan uit). Zonder gebied staat erboven "Kies eerst een gebied"; staat de tekening niet in
  meters, dan staan alle kaarten grijs en staat erboven hoe je de eenheid goed zet (zie 1). De luchtfoto, het plaatje van
  de BRT (de standaard) en het kaartbeeld van de BGT komen als beeld in een map naast de tekening: in een tekening zonder naam staat daar
  "Sla de tekening eerst op" met een knop **Opslaan**. Beta-kaarten zijn zo gemarkeerd; een driehoekje
  toont de vaste waarschuwing van een kaart.
- **Gereedschap** – een rij knoppen: AHN-punt (`VKAHNPUNT`), NAP-referentie, NAP-leider en NAP herberekenen
  (`VKNAPSET`, `VKNAPLEADER`, `VKNAPUPDATE`; in een lengteprofiel, zie 4), KLIC-levering (`VKKLIC`, met een
  bestandskiezer), Eigen grondonderzoek (`VKGEF`, met een bestandskiezer voor een of meer GEF- of XML-bestanden,
  zie 4), Naar Google Earth (`VKKMZ`; wat je al gekozen had, neemt het mee als er geen commando
  loopt, anders de VLEA-kaarten in het gebied zonder KLIC; één open lijn of polylijn wordt een
  boortracé, zie 10), KML inlezen (`VKKMLIMPORT`), Punten inlezen (`VKPUNTEN`),
  Geografische plek (`VKGEOPLEK`, zie 11), Info (`VKINFO`), Import wissen (`VKWISSEN`), Stijl (`VKSTIJL`) en
  Bijwerken (`VKUPDATE`). Elke knop doet hetzelfde als het commando, met de keuzes uit de instellingen; de uitleg
  bij de knop noemt het commando.
- **Bekijk de plek** – vier knoppen: Google Maps, Street View, StreetSmart en DINOloket. Wijs daarna een
  punt aan (Enter = midden van het beeld); de plek opent in je browser (zie 11).
- **Laatste keer geladen** – tijdens het laden staat er "wacht – zie opdrachtregel": een vraag (zoals
  [Vervangen/Erbij/Overslaan] als de kaart al in de tekening staat) komt op de opdrachtregel. Daarna per
  kaart het aantal objecten, of hoe het afliep (overgeslagen, geweigerd, mislukt, geannuleerd), met
  hoogstens tien meldingen; zijn het er meer, dan eerst de waarschuwingen, dan de rest, en "... en N
  meer (zie de opdrachtregel)". Ligt er in het gebied niets van die kaart, dan staat er "niets getekend"
  met een zin die dat zegt (bijvoorbeeld "Er liggen geen BAG-panden of -adressen binnen dit gebied."),
  geen "0".
- **Onderaan** – de bronvermelding van wat je net laadde, de disclaimer, zo nodig "Nieuwe versie
  beschikbaar" (klik = `VKUPDATE`), de versie en **Over VLEA**.

Meer kaarten in één keer laden kan met `VKLADEN` op de opdrachtregel (zie 4).

### Instellingen (tandwiel)
De keuzes staan niet op het hoofdscherm maar in het instellingenvenster:

- **Kaarten**: per kaart haar opties, bijvoorbeeld de BGT-groepen, de sondeerplots of snel/scherp bij
  de luchtfoto. Bij de BRT staat onder de naam per keuze één zin wat je krijgt, bij AHN welke AHN-versie het is
  en wat de rasterstap doet;
- **Gereedschap**: hoogte op een punt (maaiveld of met gebouwen, label met de hoogte), de breedte van
  de contour (standaard 25 m aan weerszijden), "ook een los .kml-bestand" bij Google Earth, en de
  opties van de KLIC-levering;
- **Stijl**: NLCS-kleuren of grijze onderlegger voor de kaarten (een KLIC-levering komt altijd in
  NLCS-kleuren, de sonderingen, de boringen en de peilbuizen blijven altijd in kleur), en of de bronvermelding als tekst in de tekening komt. De
  grijze onderlegger maakt lagen grijs, geen beeld: de luchtfoto, het plaatje van de BRT en het kaartbeeld van de BGT
  blijven in hun eigen kleuren. Wil je de BRT grijs, kies dan bij de BRT **Plaatje grijs**;
- **Algemeen**: één keer per dag kijken of er een nieuwe versie is, en of het palet de status van de bronnen toont
  (standaard aan; zie hieronder).

Alle aan/uit-keuzes staan standaard aan, behalve maatvoering en annotaties van de KLIC-levering (zie 6) en
grondgebruik bij de BRT (zie 4); zet uit wat je niet wilt. Een keuzelijst staat op de
standaard van de kaart of het commando (bijvoorbeeld maaiveld, het plaatje in kleur bij de BRT, NLCS-kleuren). **Opslaan**
bewaart je keuzes (in `%LOCALAPPDATA%\VLEA-AutoCAD\instellingen.json`), **Annuleren** laat alles zoals
het was en **Standaard herstellen** zet alles in het venster terug. De knoppen in het palet en op het
lint gebruiken deze keuzes; getypte commando's en scripts gebruiken de vaste standaarden (zie 4).
Opslaan bewaart alleen wat je anders kiest dan de standaard. Krijgt een keuze in een nieuwe versie een
andere standaard, dan krijg je die vanzelf, behalve als je die keuze zelf anders had gezet. Wil je het
oude gedrag terug, zet de keuze dan opnieuw; de wijzigingen bij elke versie zeggen welke keuze een
nieuwe standaard kreeg. Een keuze die niet meer in het venster staat, vervalt: bij de BRT van 0.2.3 Kaartbeeld,
de stijl van het kaartbeeld en Terrein en reliëf (zie 4, De BRT).

### Status van de bronnen (het bolletje, `VKSTATUS`)
Achter elke kaart staat een klein bolletje, en ook bij het zoeken van een adres. Het zegt of de bron van die kaart
nu antwoordt:

| Bolletje | Betekenis |
|---|---|
| groen | De bron werkt: binnen 3 seconden het antwoord dat de kaart nodig heeft. |
| oranje | De bron werkt, maar is traag (langer dan 3 seconden). Laden duurt dan waarschijnlijk ook langer. |
| rood | De bron ligt eruit: een foutmelding, geen antwoord binnen 8 seconden, of een antwoord dat niet is wat de kaart nodig heeft ("inhoud wijkt af"). |
| grijs | Nog niet gecontroleerd (net geopend, of de controle duurde te lang). |

Wijs het bolletje aan voor de uitleg, per bron één regel, bijvoorbeeld "PDOK BGT werkt (0,4 s)" of "legger
Rijkswaterstaat reageert niet: geen antwoord binnen 8 s". Een kaart met twee bronnen (BRT: TOP10NL en de
achtergrondkaart; de zones: de waterschappen en de legger van Rijkswaterstaat) krijgt de kleur van de bron die het
slechtst gaat. Het bolletje is alleen informatie: **Laden** kan altijd, ook bij rood. Ligt een bron eruit, dan kun je
niets anders doen dan het later opnieuw proberen; je krijgt geen meldingen.

Wanneer kijkt VLEA? Bij het openen van het palet, op de achtergrond (het palet werkt meteen), en hoogstens één keer
per tien minuten vanzelf: binnen die tijd toont het de vorige uitkomst. Met **Status vernieuwen** naast KAARTEN kijkt
VLEA meteen opnieuw; de uitleg bij die knop zegt hoe laat de vorige controle was. Per kaart zijn dat een of twee
kleine verzoeken (twee bij BRT en bij de zones) aan dezelfde bron als de kaart zelf: telkens één object, één
kaarttegel of één klein beeld, altijd in een vast testgebied
(de binnenstad van Amersfoort en een paar andere vaste, openbare plekken), nooit in jouw gebied. De bron ziet dus
niet waar je werkt. Staat bij de zones langs waterkeringen de optie `rws` uit, dan vraagt het palet de legger van
Rijkswaterstaat ook voor de status niet.

Uitzetten: instellingenvenster (tandwiel), **Algemeen**, "Status van de bronnen tonen". Dan zijn de bolletjes en de
knop weg en doet het palet deze verzoeken niet.

`VKSTATUS` doet dezelfde controle vanaf de opdrachtregel, altijd vers, en zet per kaart één regel op de
opdrachtregel, met onderaan hoeveel er werken. `VKSTATUS` vraagt altijd alle bronnen, ook de legger van
Rijkswaterstaat, ook als de optie `rws` of "Status van de bronnen tonen" uit staat: het is een commando dat je zelf
start. Het stelt geen vragen, dus het werkt ook in een script en in de AutoCAD-kern zonder schermen. Esc stopt het.

## 3. Een gebied kiezen
- **Adres, postcode of perceel** (`VKADRES`, of het zoekveld in het palet): typ bijvoorbeeld een
  straat met huisnummer en plaats en kies een suggestie. AutoCAD zoomt ernaartoe en VLEA stelt een
  gebied van 250 x 250 m rond dat punt voor.
- **Rechthoek aanwijzen**, **polylijn kiezen** of **coördinaten typen** (`VKGEBIED`): twee
  hoekpunten, een gesloten polylijn, of `xmin,ymin,xmax,ymax` in RD-meters.
- **Strook langs een lijn** (`VKCONTOUR`): kies een lijn, polylijn, boog, cirkel, ellips of spline (in
  Civil 3D ook een as) en geef de breedte aan weerszijden (Enter = 25 m; typen of twee punten
  aanwijzen). VLEA tekent de contour als gesloten polylijn op de laag `VLEA-KAART-GEBIED` en maakt hem
  het gebied van de tekening: kaarten laden daarna langs de strook. Een bocht krijgt aan de buitenkant
  een ronde hoek, de uiteinden een halve cirkel. Omsluit de lijn zelf een stuk grond (een lus), dan
  hoort dat stuk bij de contour: je laadt dan iets meer, nooit minder. De lijn wordt eerst iets
  vereenvoudigd: de contour wijkt hoogstens 1 % van de breedte af (25 cm bij 25 m); bij een heel
  grillige lijn meer, en dat meldt VLEA. VLEA bewaart ook de lijn zelf bij het gebied: de sonderingen
  kiezen dan de dichtstbijzijnde langs die lijn (zie 4).
- **Een strook langs een tracé:** kies bij `VKGEBIED` een gesloten polylijn om het tracé. VLEA knipt
  de kaarten dan op die polylijn (niet op de rechthoek eromheen) en haalt bij PDOK alleen de stukken
  op die de polylijn raken. De grens per kaart geldt voor wat er wordt opgehaald: bij BGT bijvoorbeeld
  de vakjes van 250 m langs de polylijn. Een schuine strook van 2 km lang en 50 m breed past zo nog
  binnen de BGT-grens; is hij te lang, dan zegt VLEA hoeveel km² de vakjes samen zijn. Kruist de
  polylijn zichzelf, dan knipt VLEA op de rechthoek en meldt dat.
- Elke tekening onthoudt haar eigen gebied, ook na opslaan en opnieuw openen.
- Het palet toont het oppervlak. Ligt het gebied buiten Nederland (buiten RD), dan zegt het palet
  dat.

## 4. Kaarten laden
- In het palet laadt **Laden** achter een kaart alleen die kaart, met de opties uit de instellingen.
- De lintknoppen **BGT**, **Kadaster**, **Luchtfoto** en **AHN** laden die ene kaart met de keuzes
  uit de instellingen (opties, stijl en bronvermelding) en vragen op de opdrachtregel het gebied;
  Enter = het opgeslagen gebied van de tekening. Zonder Civil 3D zegt **AHN** meteen "alleen Civil 3D",
  zonder eerst een gebied te vragen. Het lintpaneel **Gereedschap** heeft **KLIC**, **Eigen grondonderzoek**,
  **Google Earth**, **AHN-punt**, **NAP-leider**, **NAP herberekenen**, **Punten**, **Bijwerken** en **Help**, met dezelfde keuzes als
  het palet.
- De kaartcommando's hieronder vragen zelf naar gebied en opties. Ze gebruiken de keuzes uit de
  instellingen niet: Enter bij de opties = de standaardopties van die kaart.

| Kaart | Commando | Opties (sleutel in een script) | Max. gebied | Let op |
|---|---|---|---|---|
| BAG (panden en adressen) | `VKBAG` | `verblijfsobjecten` (adressen met huisnummer) | 1 km² | alleen bestaande en vergunde objecten; gesloopt en ingetrokken niet (wel gemeld) |
| BGT | `VKBGT` | groepen `wegen`, `water`, `panden`, `terrein`, `namen` (straatnamen en huisnummers), `overig` | 1 km² | actuele versie |
| BGT als kaartbeeld | `VKBGTBEELD` | `kaartstijl` = `achtergrond` (de standaardkeuze), `pastel`, `standaard` (felle kleuren; een van de vier waarden) of `omtrek`; in het instellingenvenster staat de keuze onder Kaarten, bij BGT als kaartbeeld, als "Stijl" | 5 km² | beta; een plaatje van de BGT naast de tekening, eerst opslaan; zie hieronder |
| BRT (topografische kaart) | `VKBRT` | `soort` = `kleur` (plaatje in kleur, zoals het portaal; de standaardkeuze), `grijs` (plaatje grijs) of `lijnen` (TOP10NL, een overzichtskaart); groepen `wegen`, `water`, `gebouwen`, `grondgebruik` (standaard uit), `relief`, `inrichting`, `namen`, `vlakken` = `randen` (de standaardkeuze) of `omtrek` en `lijnkleur` = `portaal` (de standaardkeuze) of `wit` (alleen bij `lijnen`) | 16 km² | beta; het plaatje naast de tekening, eerst opslaan; volgens het Kadaster de lijnen niet voor een schaal groter dan 1:5.000 en het plaatje niet groter dan 1:750; zie hieronder |
| Kadastrale kaart | `VKKADASTER` | `perceelnummers` | 5 km² | in een stad orde 50.000 objecten bij 5 km²: laden duurt dan langer |
| Luchtfoto | `VKLUCHTFOTO` | `scherpte` = `snel` (25 cm) of `scherp` (8 cm) | 5 km² | foto naast de tekening; eerst opslaan; bij een groot gebied wordt de pixel grover (snel tot 50 cm bij 5 km²) |
| AHN-hoogte | `VKAHN` | `model` = `dtm` (maaiveld) of `dsm` (met gebouwen en begroeiing); `stap` = `fijnst` (de standaardkeuze), `1`, `2` of `5` (m) | 4 km² | alleen Civil 3D; AHN4 (2020-2022), de enige versie bij PDOK; een hoogtemodel per gebied ("VLEA AHN RD 154750-462750 500x500"); onder panden en water geen meetpunten (het model overbrugt die plekken); zie hieronder |
| Wegen (NWB) | `VKNWB` | `hectometrering` | 25 km² | hectometerpaal als oranje bordje met het wegnummer; zie hieronder |
| Spoorwegen | `VKSPOOR` | `kilometrering` | 100 km² | beta |
| Riolering | `VKRIOOL` | `labels` (materiaal en diameter), `hoogtes` (bob bij leidingen, putnaam en maaiveld bij putten), `aansluitingen` | 4 km² | onvolledig; niet voor WIBON/KLIC; riool zonder laag in kleur 210, zoals in een KLIC-levering (zie 6, Kleur en lijndikte); zie hieronder |
| Natura 2000 | `VKNATURA2000` | | 100 km² | beta |
| Zones langs waterkeringen | `VKZONERINGEN` | `kernzone`, `beschermingszone`, `vrijeruimte` (profiel van vrije ruimte), `rws` (ook de zones van Rijkswaterstaat) | 9 km² | beta; niet elk waterschap levert zijn zones aan; een ontbrekende zone betekent niet dat er geen zone is; de legger van de beheerder is leidend (dat staat ook na het laden op de opdrachtregel); `rws` haalt bij `geo.rijkswaterstaat.nl` |
| Sonderingen (BRO) | `VKSONDERINGEN` | `sondeerplots`, `labels`, `xml`; `aantal` = `5`, `10`, `25` (de standaardkeuze), `50`, `100` of `alle` | 4 km² | beta; zonder keuze de 25 dichtstbijzijnde; zie hieronder |
| Boringen (BRO) | `VKBORINGEN` | `boorprofielen`, `labels`, `xml`; `aantal` = `5`, `10`, `25` (de standaardkeuze), `50`, `100` of `alle` | 4 km² | beta; geotechnische en geologische boringen; zonder keuze de 25 dichtstbijzijnde; boorprofielen links naast het gebied; zie hieronder |
| Peilbuizen (BRO) | `VKPEILBUIZEN` | `standen`, `labels`, `csv`, `zonderstanden`; `aantal` = `5`, `10`, `25` (de standaardkeuze), `50`, `100` of `alle` | 4 km² | beta; per filter de gemeten grondwaterstanden t.o.v. NAP; zonder keuze de 25 dichtstbijzijnde; zie hieronder |

Aan/uit-opties staan standaard aan, behalve `grondgebruik` bij de BRT; in een script schrijf je `aan` of
`uit`. Staan alle onderdelen van een kaart uit (bijvoorbeeld alle drie de zonesoorten, alle BGT-groepen of
bij de BRT als lijnen alle groepen), dan vraagt VLEA niets op, slaat die kaart over en zegt dat; een
eerdere import van die kaart blijft dan staan, ook met `vervangen=ja`.

**De grens bij een polygoon.** Bij een strook langs een tracé geldt de grens voor wat de kaart
werkelijk ophaalt: bij BGT, BAG, BRT, kadaster, NWB en riolering de vakjes langs de polygoon; bij AHN, de
sonderingen, de boringen en de peilbuizen de rechthoek om het gebied (die worden op de rechthoek bevraagd). Een lange, schuine
strook kan dus voor AHN te groot zijn terwijl hij zelf klein is: het palet, `VKGEBIED` en `VKCONTOUR`
zeggen dan al "te groot". Kies dan een kortere strook of laad AHN in delen.

**Niets in het gebied.** Ligt er van een kaart niets in het gebied, dan zegt VLEA dat in een zin, zoals
"Voor dit gebied levert PDOK geen rioleringsgegevens; niet elke gemeente levert aan GWSW." of
"BGT (topografie): niets gevonden in dit gebied.", in plaats van "0 objecten getekend". Dan komt er ook
geen bronvermelding. Mislukt het ophalen, dan staat de reden er, niet deze zin; is er daardoor niets
getekend, dan staat die reden op de opdrachtregel bovenaan, in plaats van "0 objecten getekend".

### De BRT (`VKBRT`)
`VKBRT` zet de BRT, de topografische kaart van het Kadaster, onder je tekening. Je kiest één van drie (in het palet
het tandwiel, Kaarten, BRT (topografische kaart), **Soort**; in een script `soort`):
- **Plaatje in kleur (zoals het portaal)** (`soort=kleur`, de standaardkeuze): de BRT-achtergrondkaart als
  afbeelding, met kleuren en namen; dezelfde kaart die het VLEA-portaal in een tekening zet.
- **Plaatje grijs** (`soort=grijs`): dezelfde kaart in grijstinten, rustig onder je eigen tekening.
- **Lijnen (TOP10NL, overzichtskaart)** (`soort=lijnen`): wegen, water, gebouwen, reliëf en inrichting als lijnen op
  eigen lagen (`B-WE-OG-TOPOKAART_…`), waar je op kunt vastklikken, met straat-, water- en plaatsnamen als tekst; een
  overzichtskaart, voor detailwerk is er de BGT (`VKBGT`).

Meer over elke keuze:
- **Het plaatje** komt als PNG met world-file (`.pgw`) in de map `<tekening>_kaarten` naast de tekening (sla de
  tekening eerst op), achter de rest, op de eigen laag `VLEA-KAART-BRT` (zoals in 0.2.3). Het is dezelfde kaart van
  PDOK als in het portaal, maar scherper: VLEA kiest het fijnste niveau dat binnen 16 miljoen pixels past (0,21 m per
  pixel bij 0,25 km², 0,42 m bij 1 km², 0,84 m bij 4 tot 9 km², 1,68 m bij 16 km²). De namen in het beeld zijn
  daardoor kleiner dan in het portaal. Het is een plaatje: je kunt er niet op vastklikken.
- **De lijnen** zijn de topografie van TOP10NL: wegen en water als vlakken, gebouwen als huizenblokken, en de randen
  liggen gemiddeld ruim een meter naast die van de BGT. Ze zien er dus anders uit dan de BGT of het plaatje. De
  groepen `wegen`, `water`, `gebouwen`, `grondgebruik`, `relief`, `inrichting` en `namen` en de keuzes **Vlakken** en
  **Kleur van de lijnen** gelden alleen voor de lijnen.
- **Wegen naar soort:** een weg op maaiveld staat op de laag van zijn soort. **Hoofdwegen** (in TOP10NL een
  autosnelweg, hoofdweg of regionale weg) op `B-WE-OG-TOPOKAART_WEG_HOOFDWEG-G`, **fietspaden** (alleen fietsers en
  bromfietsers, eventueel ook voetgangers) op `…_WEG_FIETSPAD-G`, **paden** (alleen voetgangers of ruiters, ook een
  voetgangersgebied) op `…_WEG_PAD-G`, en de rest (lokale weg, straat, parkeerplaats, busbaan) op `…_WEG-G`. Een
  wegdeel op een kruising van twee soorten krijgt de belangrijkste. Zo zet je bijvoorbeeld de paden in AutoCAD uit.
  Onder maaiveld staan alle wegen samen op `…_WEG_ONDER-G`.
- **Kleur van de lijnen** (`lijnkleur`): **Zoals het portaal: grijs, water blauw, gebouwen wit** (`lijnkleur=portaal`,
  de standaardkeuze): wegen, terrein, reliëf, spoor en inrichting grijs (kleur 8), water blauw (kleur 4), gebouwen wit
  (kleur 7), ook onder maaiveld; hetzelfde kleurschema als de onderleggers in het VLEA-portaal. Of **Alles wit (kleur 7,
  zoals tot en met 0.2.3)** (`lijnkleur=wit`). De kleur zit in de laag: een laag die al in je tekening staat, houdt zijn
  kleur bij opnieuw laden, alleen nieuwe lagen krijgen de gekozen kleur. Een tekening met BRT-lijnen uit 0.2.3 (alles
  kleur 7) zet je met `VKSTIJL`, **Nlcs** in de kleuren zoals het portaal. `VKSTIJL` kent de keuze **Alles wit** niet: na
  `VKSTIJL`, **Nlcs** staan ook dan de BRT-lagen in de kleuren zoals het portaal. Wil je bestaande BRT-lagen weer wit,
  zet de laagkleur zelf op 7, of wis de BRT (`VKWISSEN`, kaart `brt`), `PURGE` de lege lagen en laad opnieuw met
  **Alles wit**.
- **Namen** (`namen`, standaard aan): straatnamen (en zonder straatnaam het nummer van een autosnelweg of N-weg, zoals
  A2 of N221) op `B-WE-OG-TOPOKAART_WEGNAAM-T18`, namen van rivieren, kanalen en sloten op `…_WATERNAAM-T18`, en
  plaatsnamen (een woonkern, buurtschap of gehucht; geen wijk of buurt) op `…_PLAATSNAAM-T35`, allemaal in kleur 10 (bij
  **Alles wit** kleur 7). Straat- en waternamen zijn 18 m hoog, plaatsnamen 35 m: groot genoeg voor een overzichtskaart,
  te groot om in te zoomen tot op de straat. Elke naam staat rechtop leesbaar: langs de straat of het smalle water in het
  midden van het langste stuk, in breder water in het water langs de lange kant, een plaatsnaam waterpas midden in de
  plaats. Per stuk straat (de delen met dezelfde naam die op elkaar aansluiten) één naam, en dezelfde naam niet nog eens
  binnen 540 m: twee rijbanen of de op- en afritten van een snelweg krijgen samen één naam. Namen raken elkaar niet en
  liggen helemaal binnen het gebied, ook bij een gekozen polylijn of strook met een inham; eerst de plaatsen, dan het
  water, dan de straten van lang naar kort. Is een straat binnen het gebied korter dan zijn naam, of past de naam nergens
  zonder een andere te raken, dan komt hij er niet; de melding na het laden zegt hoeveel namen dat waren. In een
  stadscentrum krijgt zo ongeveer één op de vijf straten een naam; wil je elke straatnaam, laad dan de BGT (`VKBGT`, groep
  `namen`). Straatnamen komen alleen mee met de wegen
  (`wegen=aan`), waternamen alleen met het water (`water=aan`); wat onder maaiveld ligt, krijgt geen naam. Voor de namen
  haalt VLEA ook de hartlijnen van de wegen en de plaatsen op; die komen zelf niet in de tekening. Wis je met `VKWISSEN`,
  **Selectie** een straatnaam, dan gaat het stuk weg eronder mee (in TOP10NL hetzelfde object), net als een huisnummer bij
  de BGT; met `ERASE` haal je alleen de naam weg. Wil je geen namen: zet **Namen** uit of typ `namen=uit`.
- **Grondgebruik** (`grondgebruik`, standaard uit): de grenzen tussen grasland, bos, bebouwd gebied en ander terrein,
  op `B-WE-OG-TOPOKAART_TERREIN-G`. Op het plaatje zijn dat alleen kleurovergangen; als lijnen waren ze het grootste deel
  van een drukke kaart. Zet het aan als je bijvoorbeeld een bosrand nodig hebt. **Reliëf** (`relief`, standaard aan):
  taluds en hoogteverschillen, op `…_RELIEF-G`. Een script van 0.2.3 met `terrein=aan` of `terrein=uit` werkt nog en zet
  die twee samen, behalve wat je in hetzelfde commando zelf typt (`terrein=uit,relief=aan` geeft alleen het reliëf).
- **Onder maaiveld:** een weg in een tunnel of onder een viaduct, een duiker, overkluisd water of een ondergrondse
  parkeergarage (in TOP10NL een hoogteniveau onder 0) staat gestreept op een eigen laag met `_ONDER` in de naam:
  `…_WEG_ONDER-G`, `…_WATER_ONDER-G`, `…_SPOOR_ONDER-G`, `…_GEBOUW_ONDER-G`, `…_TERREIN_ONDER-G`, `…_RELIEF_ONDER-G`
  en `…_INRICHTING_ONDER-G` (lijntype `ZZ-HIDDEN-SO`), punten op `…_GEBOUW_ONDER-S` en `…_INRICHTING_ONDER-S`. Ze
  vallen niet weg: voor een boring is een duiker of tunnel juist informatie, maar ze lezen niet als een rand die je ziet.
  Voor de precieze ligging is TOP10NL niet nauwkeurig genoeg; kijk daarvoor in de BGT. Zet je de `_ONDER`-lagen uit,
  dan zie je alleen wat op maaiveld ligt.
- **Vlakken: Randen, elke rand één keer** (`vlakken=randen`, de standaardkeuze): wegen, water en terrein bedekken samen
  het hele land, in stukken. VLEA tekent ze als randen. Een rand die twee vlakken delen, staat er één keer, op de laag
  van het vlak dat voorgaat: een gebouw, dan water, dan weg (hoofdweg, weg, fietspad, pad), dan terrein. Een naad tussen
  twee wegdelen van dezelfde soort, twee stukken water of twee terreinvlakken met hetzelfde grondgebruik staat er niet
  in, dus geen dwarsstreepjes over de weg. De rand tussen twee soorten weg staat er wel, één keer: zo zie je een
  fietspad langs de rijbaan, en ook waar een fietspad, pad of zijstraat aansluit. Langs de rand van het gebied komt geen
  kaderlijn. Gebouwen houden hun gesloten omtrek.
  - Wegen, water en terrein zijn daardoor meestal geen gesloten polylijnen: oppervlak of omtrek aflezen kan op die
    lijnen niet. Klik je op zo'n lijn, dan staat in `VKINFO` `vk_zijden: deels`. Een vlak dat al zijn randen houdt en
    binnen het gebied ligt, blijft gesloten.
  - Een vlak zonder eigen rand (bijvoorbeeld een kruising die aan vier kanten aan een ander wegdeel grenst) komt niet
    in de tekening; de melding na het laden zegt hoeveel.
  - Een rand staat maar op één laag. Zet je in AutoCAD de laag van de gebouwen uit, dan mist ook het stuk wegrand
    langs die gebouwen. Wil je wegen zonder gebouwen, zet dan bij het laden **Gebouwen** uit (`gebouwen=uit`): dan krijgt
    de weg zijn hele rand.
- **Vlakken: Gesloten omtrek per vlak** (`vlakken=omtrek`): elk vlak als gesloten polylijn, ook langs de rand van het
  gebied, zoals tot en met 0.2.3. Elke rand tussen twee vlakken staat er dan twee keer.
- **Een script van 0.2.3** blijft werken: `soort=vector` geeft de lijnen (wel met de lagen, kleuren en namen van nu),
  `soort=kaartbeeld` het plaatje in grijs (zoals toen), en `soort=kaartbeeld,kaartstijl=standaard` (of `grijs`,
  `pastel`, `water`) het plaatje in die stijl. Pastel en water kun je alleen zo nog kiezen. `kaartstijl` bij een
  andere soort doet niets; VLEA zegt dat na het laden. In het instellingenvenster staan Kaartbeeld, de stijl van het
  kaartbeeld en Terrein en reliëf niet meer: had je die in 0.2.3 gekozen, dan krijg je het plaatje in kleur (ook als
  dat kaartbeeld grijs was) en staat het reliëf aan. Kies dan **Plaatje grijs** of zet **Reliëf** uit.
- **Precies de lijnen van 0.2.3** (dezelfde lijnen, op dezelfde lagen, alles kleur 7, zonder namen): typ
  `soort=lijnen,vlakken=omtrek,grondgebruik=aan,lijnkleur=wit,namen=uit`, of kies in het instellingenvenster bij de BRT
  **Soort: Lijnen**, **Vlakken: Gesloten omtrek per vlak**, **Grondgebruik** aan, **Kleur van de lijnen: Alles wit** en
  **Namen** uit. Voeg daarna in AutoCAD met `LAYMRG` de drie wegsoorten (`…_WEG_HOOFDWEG-G`, `…_WEG_FIETSPAD-G` en
  `…_WEG_PAD-G`) samen met `…_WEG-G`, en elke `_ONDER`-laag met haar gewone laag (bijvoorbeeld `…_WEG_ONDER-G` met
  `…_WEG-G`); staat die gewone laag niet in je tekening, hernoem de nieuwe dan met `RENAME`. Dat moet na elke keer
  laden opnieuw: VLEA tekent altijd op de nieuwe lagen.
- **Grijze onderlegger:** die maakt lagen grijs, geen plaatje. Het plaatje in kleur blijft in kleur onder een grijze
  tekening; wil je de BRT grijs, kies dan **Plaatje grijs**. De lijnen worden wel grijs.
- **Opnieuw laden:** het plaatje en de lijnen tellen als dezelfde kaart (sleutel `brt`). Vervangen wist dus ook een
  eerder plaatje of eerdere lijnen in dat gebied, en de vraag zegt dat. Wil je beide, kies dan **Erbij**.

### De BGT als kaartbeeld (`VKBGTBEELD`)
`VKBGTBEELD` zet de BGT als afbeelding onder de tekening, zoals de luchtfoto: PDOK maakt het kaartbeeld, VLEA
voegt de tegels samen en zet ze als beeld op de laag `VLEA-KAART-BGT`, achter alle andere objecten. Het is een
**tweede kaart naast `VKBGT`**: die blijft de BGT als lijnen, vlakken, bomen en huisnummers op NLCS-lagen, waar je
op kunt vastklikken en meten. Het kaartbeeld is een **plaatje**: je kunt er niet op vastklikken. Het rustiger
kaartbeeld van de BRT in kleur krijg je met `VKBRT` (de standaardkeuze, zie hierboven).
- **Kaartstijl** (in het instellingenvenster onder Kaarten, bij BGT als kaartbeeld, heet de keuze "Stijl"; dat is
  niet het hoofdstuk Stijl voor NLCS-kleuren of grijs; in een script `kaartstijl`): `achtergrond` (de standaardkeuze:
  zachte kleuren, het echte BGT-beeld met erven, stoepen en huisnummers; de huisnummers staan er alleen bij 0,42 m
  per pixel of scherper, dus bij een gebied tot ongeveer 2,8 km², zie "Niveau en pixel"), `pastel` (een rustige
  onderlegger in wit en lichtgrijs), `standaard` (felle kleuren; een van de vier waarden, niet de standaardkeuze) of
  `omtrek` (alleen lijnen, bedoeld op een doorzichtige achtergrond, bijvoorbeeld boven een luchtfoto: laad de
  luchtfoto eerst; de bedoeling is dat een later geladen beeld boven een eerder geladen beeld komt. Ligt de omtrek
  toch onder de foto, zet hem dan met `DRAWORDER` bovenaan).
- **Eerst opslaan.** Het beeld komt als PNG met world-file (`.pgw`) in de map `<tekening>_kaarten` naast de
  tekening, als `bgtbeeld_<stijl>_n<niveau>_<x>_<y>_<x>_<y>.png`. Stuur die map mee als je de tekening deelt.
- **Niveau en pixel.** VLEA kiest het fijnste niveau waarop het gebied binnen 16 miljoen pixels blijft: bij 0,25 km²
  0,21 m per pixel, bij 1 km² 0,42 m, bij 5 km² (de grens) 0,84 m, en bij een klein gebied tot 0,05 m. Is het beeld
  grover dan 0,21 m, dan zegt VLEA dat; een kleiner gebied geeft een scherper beeld. Grover dan 0,84 m kan niet: PDOK
  levert daaronder geen kaartbeeld. Past het gebied op 0,84 m niet binnen het budget (kan bij een lang, schuin tracé,
  ook al is het oppervlak klein), dan weigert VLEA met "kies een kleiner gebied" in plaats van een wit beeld te maken.
- **Duur en grootte** (gemeten op 02-10-2026 in Amersfoort en Rotterdam): 0,25 km² ongeveer 7 s en 2 MB (100
  kaarttegels), 1 km² 15 tot 30 s en 3 tot 4 MB, 5 km² ongeveer 50 s en 6 tot 7 MB (120 tot 145 kaarttegels); het
  grootste beeld dat we maten was ongeveer 10 MB. Esc annuleert; de beelden die dan al waren weggeschreven, haalt
  VLEA weer weg.
- **Strook langs een tracé:** alleen de beelden die de strook raken worden opgehaald; een tegel in zo'n beeld die de
  strook niet raakt, blijft leeg (wit; bij `omtrek` bedoeld als doorzichtig).
- Opnieuw laden (Vervangen, Erbij of Overslaan), `VKINFO` en `VKWISSEN` werken zoals bij elke kaart (sleutel
  `bgtbeeld`). `VKSTIJL` (grijze onderlegger) laat het beeld ongemoeid: een afbeelding heeft geen laagkleur.
- Bronvermelding: Kadaster, CC BY 4.0, bewerkt. De kaart is beta tot ze in AutoCAD is geprobeerd: dat de omtrek
  doorzichtig is en dat een later geladen beeld boven een eerder geladen beeld komt, is de bedoeling en is nog niet
  in AutoCAD gezien.

### Sonderingen (BRO)
`VKSONDERINGEN` haalt de sonderingen (CPT) uit de Basisregistratie Ondergrond (BRO) in het gebied.
Het palet zet ze onder **Grondonderzoek**.
- **Hoeveel sonderingen** (optie `aantal`): VLEA tekent hoogstens **25 sonderingen**: de 25 het dichtst bij
  het midden van het gebied. Tot en met 0.2.2 kwamen alle sonderingen in het gebied; op een plek met veel
  sonderingen waren dat duizenden objecten. Liggen er meer dan 25, dan zegt de melding hoeveel er niet
  getekend zijn, hoe ver de verste van het midden ligt en hoe je meer krijgt, bijvoorbeeld "25 van de 69
  sonderingen in het gebied getekend: de 25 dichtst bij het midden van het gebied (de verste ligt 162 m van
  het midden)".
  - Meer of minder: in het palet het tandwiel, Kaarten, Sonderingen (BRO), **Aantal sonderingen (de
    dichtstbijzijnde)**: hoogstens 5, 10, 25, 50 of 100, of alle in het gebied. Bij het commando de optie
    `aantal`, bijvoorbeeld `aantal=10` of `aantal=alle` (een ander getal dan uit de lijst weigert VLEA).
  - De regel: de afstand tot het midden van het gebied, op een decimeter. Liggen twee sonderingen even ver,
    dan gaat de diepste voor (de einddiepte), daarna het laagste BRO-id.
  - **Bij een strook van `VKCONTOUR` telt de afstand tot de lijn** waar de strook omheen ligt, niet tot één
    punt in het midden: je krijgt de sonderingen langs het hele tracé, ook bij de uiteinden. De melding zegt
    dat ("de 12 dichtst bij de lijn van de contour (de verste ligt 31 m van de lijn)"). De lijn staat bij het
    gebied in de tekening, ook na opslaan en opnieuw openen.
  - Een eigen gesloten polylijn (`VKGEBIED`) of een contour van vóór deze versie heeft geen lijn: dan telt
    het midden, en dat is bij een polylijn het punt in het gebied dat het verst van de rand ligt. Bij een
    lange strook ligt dat ergens op het tracé; maak de strook dan opnieuw met `VKCONTOUR`.
  - Een andere keuze: laad opnieuw; Enter bij [Vervangen/Erbij/Overslaan] vervangt de vorige keuze.
- Elke gekozen sondering komt als symbool (een schuin kruisje van 1,6 x 1,6 m, blok `VK_SONDERING_KRUIS`) op
  `B-WE-MO-ONDERZOEK_SONDERING-S`, met rechts ervan een label op `B-WE-MO-ONDERZOEK_SONDERING-T35` (oranje, kleur
  30): het volgnummer van de plot, het BRO-id, het maaiveld t.o.v. NAP, de einddiepte en de datum (optie `labels`).
  De volgnummers lopen van west naar oost; liggen twee sonderingen precies even ver naar het oosten, dan eerst de
  zuidelijke.
- **Sondeerplots** (optie `sondeerplots`): per sondering een grafiek rechts naast het gebied, in rijen
  van vijf, nooit over de kaart. Verticaal 1:1 in meters t.o.v. NAP (een label per meter, zonder plusteken, en de
  astitel `DIEPTE (m) t.o.v. NAP`), een raster van 1 x 1 m (grijs, kleur 253) met links van het meetgebied een
  aanloopstrook van 1 m: een streepje op elke meter sondeerlengte, vanaf maaiveld tot de einddiepte (kleur 7). Verder
  de conusweerstand (0-30 MPa over 20 m, blauw, kleur 5), de
  plaatselijke wrijving (0-0,20 MPa, rood, kleur 1) en het wrijvingsgetal (15-0 %, gespiegeld in de
  rechterhelft, donkercyaan, kleur 134). Meet de sondering ook de waterspanning achter de conus (u2), dan komt
  er een vierde lijn bij: de waterdruk, -0,08 tot 0,12 MPa over 20 m (kleur 7), ook onder nul, met een eigen
  schaalregel onderaan de kop. In de kop heeft elke lijn een schaalregel: de naam in hoofdletters (de
  conusweerstand heet daar PUNTDRUK, net als de laag), de getallen en een as met een streepje op elke meter, in de
  kleur van de lijn; een dubbele grijze lijn scheidt de kop van het raster. De plots in één rij hebben dezelfde
  NAP-schaal, zodat je ze naast elkaar kunt vergelijken. Onder de plot staat links het volgnummer groot ("3."; het
  staat ook in het label op de kaart), rechts daarvan het BRO-id met maaiveld, datum en kwaliteitsklasse, en daaronder
  "Bron: BRO". Komen de waarden boven de schaal (bij de waterdruk ook eronder), dan wordt die 2, 4 of 8 keer zo ruim;
  het wrijvingsgetal niet. Dat staat onder de plot ("Let op: schaal verruimd (puntdruk x2, wrijving x1)"), net als
  waarden die zelfs daarbuiten komen (daar is de lijn onderbroken) en meetregels zonder diepte die niet getekend zijn.
  De teksten zijn bedoeld voor afdrukken op 1:200.
- Lagen van de plot: de lijnen staan op `B-WE-MO-ONDERZOEK_SONDERING_PUNTDRUK-GD` (conusweerstand),
  `…_WRIJVING-GD`, `…_WRIJVINGSGETAL-GD` en `…_RASTER-GD`, met lijndikte 0,25 mm (NLCS-element GD, een lijn in een
  doorsnede); de teksten van de plot staan net als het label op `B-WE-MO-ONDERZOEK_SONDERING-T35`, oranje en 0,35
  mm. De waterdruk staat op `…_WATERDRUK-GD` (kleur 7), de streepjes van de aanloopstrook op `…_SONDEERLENGTE-GD`
  (kleur 7). Een laag komt pas in je tekening als er iets op staat. De T35-laag is hier de laag van de teksten van de
  sondering; de teksten houden de teksthoogte van de plot (0,35 m, het volgnummer 1,5 m, de regel met het BRO-id 0,5
  m, het label op de kaart 0,9 m) en zijn dus geen 3,5 mm op papier: op 1:200 is een gewone tekst van de plot 1,75 mm.
  De lagen hadden tot en met 0.2.3 andere namen; oud → nieuw en hoe je de oude namen terugkrijgt, staat in de
  wijzigingen bij versie 0.2.4.
- De grijze onderlegger (instellingen of `stijl=grijs`) laat de sonderingen in kleur: in grijs zijn de lijnen van de
  plot niet uit elkaar te houden. Grijs kan daarna met `VKSTIJL`, Grijs.
- Hoogstens **25 plots per keer**: de eerste 25 van de getekende sonderingen, de dichtstbijzijnde eerst.
  Teken je er meer (`aantal` 50, 100 of alle), dan krijgen de andere alleen symbool en label; wil je van die
  een plot, kies dan een kleiner gebied rond die sonderingen. Een sondering zonder maaiveldhoogte of met
  een hoogte die niet t.o.v. NAP is, krijgt geen plot en kost geen plek; de melding noemt haar.
- De BRO-bestanden (XML) van de sonderingen met een plot komen in de map
  `<tekening>_kaarten\sonderingen` naast de tekening (optie `xml`; sla de tekening eerst op).
- **Storing bij de BRO**: antwoordt de BRO niet, of met een foutmelding in plaats van een zoekantwoord, dan wordt er
  niets getekend en zegt de melding dat het zoeken bij de BRO niet lukte, bijvoorbeeld "(het antwoord van de BRO was
  onleesbaar)". "Er ligt geen sondering uit de BRO binnen dit gebied" komt alleen als de BRO dat echt antwoordt.
  Probeer het later opnieuw; het bolletje achter de kaart zegt of de BRO weer werkt.
- De sonderingen zijn informatief; controleer datum en kwaliteitsklasse (in de plot en in `VKINFO`)
  voordat je ze gebruikt. De dichtstbijzijnde sondering is niet vanzelf de beste: een diepere of nieuwere
  kan net buiten de keuze vallen. Kies dan een hoger aantal of een kleiner gebied.

Een script, één regel per vraag (een vak bij het station van Amersfoort; daar lagen op 29-09-2026 69
sonderingen):

```text
VKSONDERINGEN
C
153944,462553,154444,463053
aantal=10,vervangen=ja
```

#### Sonderingen weghalen
Eén of een paar sonderingen te veel in de tekening? Typ `VKWISSEN` (in het palet **Import wissen**) en kies
`Selectie`. Klik het symbool, een labelregel of de plot van de sondering aan, of trek een venster over meer
sonderingen, en druk op Enter.
- Per gekozen sondering gaan het symbool, alle labelregels en de hele sondeerplot samen weg. De melding
  noemt het aantal sonderingen en objecten, bijvoorbeeld "2 sonderingen weggehaald (222 objecten: symbool,
  label en plot)". `U` maakt het ongedaan.
- De andere plots schuiven niet op: in de rij blijft een plek leeg en de volgnummers blijven zoals ze
  waren. Wil je weer een nette rij, laad dan opnieuw met Vervangen; dan komen ook de weggehaalde sonderingen
  terug (kies eerst een lager `aantal` of een kleiner gebied als je ze niet wilt).
- De BRO-bestanden (XML) in de map naast de tekening blijven staan.
- Alle sonderingen weg: `VKWISSEN` en dan `sonderingen`.

Meer over `Selectie`, ook voor andere kaarten: zie 5.

### Eigen grondonderzoek (`VKGEF`)
Nieuw in 0.2.5. `VKGEF` (in het palet en op het lint de knop **Eigen grondonderzoek**, bij het gereedschap) zet je
eigen sonderingen en boringen in de tekening: GEF-bestanden (`.gef`) van een sondeerbedrijf of uit je archief, of een
sondering uit de BRO als XML (`.xml`, zoals de BRO haar levert, bijvoorbeeld uit DINOloket). De bestanden blijven op
je eigen pc: VLEA leest ze van je schijf, maakt geen verbinding en stuurt niets naar VLEA. Er hoeft geen gebied
gekozen te zijn: elk onderzoek komt op de plek uit het bestand. Laad je in dezelfde tekening ook kaarten, sonderingen
of boringen uit de BRO, **kies dan eerst het gebied** en doe daarna `VKGEF`: alleen dan weet `VKGEF` waar die komen en
houdt het die plek vrij (zie hieronder).
- **Bestanden kiezen:** met schermen opent een venster waarin je meer bestanden tegelijk kiest (hoogstens 500 per
  keer). In een script, met `FILEDIA` 0 of in de AutoCAD-kern vraagt `VKGEF` één pad op de opdrachtregel en daarna
  de opties (zie hieronder). Een map kiezen kan niet; kies de bestanden zelf.
- **Een sondering** (GEF-CPT) komt er precies zo uit als een sondering van `VKSONDERINGEN` (zie hierboven): het
  schuine kruisje met label, en een sondeerplot in de rij rechts naast de punten, op dezelfde lagen en met dezelfde
  kop, aanloopstrook, schalen, waterdruk en onderkant. Onder de plot staat `Bron: eigen grondonderzoek (GEF)`, bij
  een XML `Bron: BRO (eigen XML-bestand)`. Is er een gebied gekozen, dan blijft rechts naast dat gebied een volle rij
  vrij voor de sondeerplots van `VKSONDERINGEN` (175 m, vijf plots breed) en komen de plots van `VKGEF` daar rechts
  naast. Ook het gebied zelf blijft vrij, en links ervan de rij voor de boorprofielen van `VKBORINGEN` (165 m): liggen
  je punten buiten het gebied, dan komt een plot die in het gebied of in een van die stroken zou vallen ook rechts van
  de strook voor de sondeerplots (dan staat hij verder van zijn punt; het volgnummer in het label zegt welke plot bij
  welk punt hoort). Zo liggen de plots van `VKGEF` nooit over die van de BRO, nooit over een boorprofiel en nooit in
  het gebied, in welke volgorde je ook inleest, zolang het gebied vóór `VKGEF` gekozen is. Laad je geen sonderingen
  of boringen uit de BRO, dan blijven die stroken leeg. De volgnummers lopen van west naar oost, zoals bij de BRO; ze beginnen bij
  elke keer `VKGEF` weer bij 1, los van de sonderingen uit de BRO in dezelfde tekening (het nummer onder de plot
  zegt welke het is).
  - Welke kolommen: VLEA zoekt ze op het grootheidnummer in de kop (`#COLUMNINFO`): 1 sondeerlengte,
    2 conusweerstand, 3 wrijving, 4 wrijvingsgetal, 6 waterspanning u2 en 11 gecorrigeerde diepte; de volgorde van
    de kolommen maakt niet uit. De diepte is de gecorrigeerde diepte, anders de sondeerlengte (dat staat dan onder
    de plot). Ontbreekt het wrijvingsgetal, dan rekent VLEA het uit (wrijving / conusweerstand), en dat staat onder
    de plot. Drukken in kPa of bar worden MPa.
  - De datum is `#STARTDATE`. Staat die er niet in, dan blijft de datum leeg (in label, attribuut en plot) en zegt
    de opdrachtregel dat; de datum van het bestand (`#FILEDATE`) gebruikt VLEA niet, want dat is vaak de dag van de
    export, jaren na de sondering.
  - Geen plot, wel een punt met label, als de hoogte van het maaiveld ontbreekt of niet t.o.v. NAP is (`#ZID` moet
    31000 zijn), als er geen meetwaarden in staan, of als de diepte niet kan kloppen; de melding zegt waarom.
- **Een boring** (GEF-BORE) komt als punt met label, precies zoals een boring van `VKBORINGEN` (zie Boringen
  (BRO)): de cirkel (blok `VK_BORING`) op `B-WE-MO-ONDERZOEK_BORING-S` en het label (nummer en soort, maaiveld,
  einddiepte en datum) op `B-WE-MO-ONDERZOEK_BORING-T35`. Zet je de laag van de boringen uit, dan gaan dus ook je
  eigen boringen uit beeld. In het attribuut `BRO_ID` staat het nummer uit het bestand; `REGISTER` en `NR` blijven
  leeg. Een boorprofiel tekent `VKGEF` nog niet.
- **Een ander soort** GEF-bestand komt als punt met label: een cirkel met een rechtop staand kruis (blok
  `VK_ONDERZOEKSPUNT`, even groot als het kruisje van een sondering, zodat je ze uit elkaar houdt), met het nummer en
  de soort, het maaiveld, de einddiepte en de datum, op de lagen van de sonderingen.
- **De plek** moet in RD staan: `#XYID` met code 31000 of 28992. Noemt het bestand geen stelsel (code 00000) en
  vallen de coördinaten in Nederland, dan leest VLEA ze als RD, zegt dat per bestand en na het tekenen nog een keer
  ("Controleer de plek"), en zet bij het punt `vk_ligging` (zie `VKINFO`). Elk ander stelsel wijst VLEA af. Een XML
  zonder RD-positie wordt omgerekend uit ETRS89 (binnen een meter).
- **Het nummer** is `#TESTID` (bij een XML het BRO-id), anders de naam van het bestand. In de tekening komt alleen
  wat ook bij een sondering uit de BRO staat (nummer, soort, plek, maaiveld, dieptes, datum, klasse en de
  meetwaarden): geen bedrijf, project of opdrachtgever, en de naam van het bestand alleen als die het nummer is
  (het bestand heeft zelf geen `#TESTID`). In het logboek komen alleen aantallen.
- **Per bestand** zegt de opdrachtregel of het is ingelezen, en anders waarom niet, bijvoorbeeld "niet ingelezen: de
  plek staat niet in RD-coördinaten" of "het is een KLIC-levering; lees die in met VKKLIC". Daarna een samenvatting.
- **Opnieuw inlezen:** staat een nummer al in de tekening, dan vraagt `VKGEF` één keer voor alle bestanden
  [Vervangen/Erbij/Overslaan]. Vervangen wist de eerdere versie van precies dat nummer (punt, label en plot); een
  ander nummer, een kaart of een KLIC-levering nooit. Erbij tekent het er nog een keer bij; Overslaan tekent alleen
  wat er nog niet stond. Enter is Vervangen, behalve als al die nummers in de tekening op een andere plek staan
  (meer dan een meter verderop): dan is het bijna altijd een ander onderzoek met hetzelfde nummer (S01 van een
  andere opdracht) en is Enter Erbij. De vraag noemt die nummers; kies Vervangen als je de plek zelf hebt verbeterd.
- **Weghalen:** `VKWISSEN` met `eigenonderzoek` wist alles wat `VKGEF` tekende, ook de bronvermelding. Met
  `Selectie` gaan van een aangewezen onderzoek punt, label en plot samen weg.
- **Bronvermelding:** "Bron: Eigen grondonderzoek (bestand van de gebruiker), ingelezen 09-10-2026", in de
  tekeningeigenschappen en (optie `bronvermelding`) als tekst onder de punten.

In een script, één regel per vraag, met `FILEDIA` op 0, zoals bij `VKKLIC` (zie 6). Staat er een spatie in het
pad, zet het pad dan tussen aanhalingstekens. Per keer één bestand; voor meer bestanden herhaal je de drie regels
vanaf `VKGEF`:

```text
FILEDIA
0
VKGEF
C:\Grondonderzoek\S01.gef
vervangen=ja
FILEDIA
1
```

### Boringen (BRO)
`VKBORINGEN` haalt de boringen uit de Basisregistratie Ondergrond (BRO) in het gebied, met per boring een
boorprofiel: een kolom met de grondsoorten, in kleur, met de code van elke laag en de diepte t.o.v. NAP. Het palet
zet ze onder **Grondonderzoek**, net als de sonderingen.
- **Welke boringen**: uit twee registers van de BRO: het geotechnisch booronderzoek (BHR-GT, boringen voor de
  geotechniek) en het geologisch booronderzoek (BHR-G, met de oude boringen uit het archief van TNO). Dat zijn
  dezelfde twee als de boringen in het portaal van VLEA. Het bodemkundig booronderzoek (BHR-P: ondiepe boringen
  voor de bodemkaart, meestal tot 1,2 m) zit er niet in. Niet elke oude boring uit het archief van TNO staat al in
  de BRO: staat een boring wel in DINOloket (`VKDINO`) maar niet in de BRO, dan tekent VLEA haar niet.
- **Hoeveel boringen** (optie `aantal`): net als bij de sonderingen hoogstens **25**, de 25 het dichtst bij het
  midden van het gebied (bij een strook van `VKCONTOUR`: bij de lijn), met dezelfde keuzes (5, 10, 25, 50, 100 of
  alle) en dezelfde regel: bij gelijke afstand de diepste eerst, daarna het laagste BRO-id. Liggen er meer, dan
  zegt de melding hoeveel er niet getekend zijn en hoe je meer krijgt.
- Elke gekozen boring komt als symbool (een cirkel van 1,6 m doorsnede, blok `VK_BORING`) op
  `B-WE-MO-ONDERZOEK_BORING-S`, met rechts ervan een label op `B-WE-MO-ONDERZOEK_BORING-T35` (oranje, kleur 30): het
  volgnummer van het boorprofiel, het BRO-id, het maaiveld t.o.v. NAP, de einddiepte en de datum (optie `labels`).
  Staan er meer boringen op (bijna) dezelfde plek, dan komen hun labels onder elkaar. De volgnummers lopen van west
  naar oost, net als bij de sondeerplots.
- **Boorprofielen** (optie `boorprofielen`): per boring een kolom van 2 m breed **links naast het gebied**, in rijen
  van tien, nooit over de kaart. Links, zodat ze nooit over de sondeerplots vallen (die staan rechts). Het laatste
  profiel van elke rij staat 25 m van het gebied; heb je minder dan tien boringen, dan staan ze dus direct naast het
  gebied. Verticaal 1:1
  in meters t.o.v. NAP, met links een as met een streepje en een getal op elke hele meter en de astitel `DIEPTE (m)
  t.o.v. NAP`; de profielen in één rij hebben dezelfde NAP-schaal. Elke laag is gevuld in de kleur van de
  hoofdgrondsoort, zoals de boringen in het portaal: **zand** geel (kleur 2), **klei** groen (3), **veen** bruin
  (34), **grind** oranje (30), **leem en silt** olijf (42), en grijs (9) voor een laag zonder grondsoort of met een
  andere hoofdnaam. Rechts van de kolom staat de code van de grondsoort volgens NEN 5104: de hoofdletter van de
  hoofdnaam (Z zand, K klei, V veen, G grind, L leem) met de bijmengingen erachter (s siltig, z zandig, k kleiig, g
  grindig, h humeus; 1 zwak, 2 matig, 3 sterk, 4 uiterst), bijvoorbeeld `Zs1` (zwak siltig zand), `Kz3` (sterk
  zandige klei), `Vm` (mineraalarm veen). Beschrijft een boring haar lagen volgens NEN-EN-ISO 14688 (nieuwere
  geotechnische boringen), dan volgt de code hetzelfde schema (`Si` is silt; zonder gradatie als de naam die niet
  heeft); dat staat onder het profiel. Een naam met "met" (bijvoorbeeld kleiig zand met grind) is de grondsoort vóór
  "met": zand, met een gele vulling, en wat na "met" komt staat zonder gradatie achter de code (`Zkg`; zwak zandige
  klei met grind wordt `Kz1g`). Is een laag te dun voor een code die niet over de vorige valt, dan staat er
  geen code (onder het profiel staat hoeveel); de vulling en `VKINFO` zeggen dan welke grondsoort het is. Boven de
  kolom het maaiveld ("mv +1,21"); onder het profiel het volgnummer groot, het BRO-id, maaiveld en datum, "Bron: BRO
  (BHR-GT)" of "(BHR-G)" en de opmerkingen. Een stuk zonder beschrijving (bijvoorbeeld de bovenste meter van een
  oude boring) blijft wit en staat onder het profiel ("Niet beschreven: 0,00-0,60 m"): VLEA verzint niets.
- Lagen van het profiel: de vullingen staan per hoofdgrondsoort op een eigen laag: `B-WE-MO-ONDERZOEK_BORING_ZAND-V`,
  `…_KLEI-V`, `…_VEEN-V`, `…_GRIND-V`, `…_LEEM-V` en `…_OVERIG-V` (NLCS-element V, een vlakvulling; de kleur staat
  op de laag, dus een grondsoort zet je apart aan of uit, of geef je in het lagenbeheer een andere kleur). De rand
  van de kolom en de grenzen tussen de lagen staan op `…_KOLOM-GD` (kleur 7), de NAP-as en de maaiveldlijn op
  `…_RASTER-GD` (grijs, kleur 253), alle teksten op `B-WE-MO-ONDERZOEK_BORING-T35`. Teksthoogtes zoals de sondeerplot:
  bedoeld voor afdrukken op 1:200.
- `VKINFO` op een vulling geeft de laag: boven- en ondergrens (m onder maaiveld), de naam van de BRO (NEN 5104
  en/of NEN-EN-ISO 14688), de code, de omschrijving in gewone woorden, of de laag opgebracht is en een bijzonder
  bestanddeel zoals puin.
- De grijze onderlegger laat de boringen in kleur, net als de sonderingen. Grijs kan daarna met `VKSTIJL`, Grijs.
- Hoogstens **25 boorprofielen per keer**, de dichtstbijzijnde eerst. Een boring zonder maaiveldhoogte, met een
  hoogte die niet t.o.v. NAP is of zonder beschreven lagen krijgt geen profiel en kost geen plek; de melding noemt
  haar.
- De BRO-bestanden (XML) van de boringen met een profiel komen in de map `<tekening>_kaarten\boringen` naast de
  tekening (optie `xml`; sla de tekening eerst op).
- **Storing bij de BRO**: lukt het zoeken in een van de twee registers niet (de BRO antwoordt niet, of geeft een
  foutmelding in plaats van een zoekantwoord), dan tekent VLEA de boringen uit het andere register en zegt een
  waarschuwing dat er boringen kunnen ontbreken, bijvoorbeeld "zoeken lukte niet in 1 deel/delen (geologische
  boringen: het antwoord van de BRO was onleesbaar)". Lukt het in geen van beide, dan wordt er niets getekend en zegt
  de melding waarom. "Er ligt geen boring uit de BRO binnen dit gebied" komt alleen als de BRO dat echt antwoordt.
  Probeer het later opnieuw; het bolletje achter de kaart zegt of de BRO weer werkt.
- De boringen zijn informatief: controleer datum, beschrijving en kwaliteit (`VKINFO`) voordat je ze gebruikt. Een
  oude boring uit het archief is vaak met de hand beschreven en minder precies dan een nieuwe.
- Weghalen gaat zoals bij de sonderingen: `VKWISSEN`, keuze `Selectie`, een deel van de boring aanklikken (symbool,
  label, een vulling of een tekst van het profiel); symbool, label en het hele boorprofiel gaan samen weg, de andere
  profielen schuiven niet op. Alle boringen weg: `VKWISSEN` en dan `boringen`.

Een script, één regel per vraag (een vak langs de A28 bij Amersfoort; daar lagen op 09-10-2026 twee geotechnische
boringen):

```text
VKBORINGEN
C
158648,468978,159148,469478
aantal=10,vervangen=ja
```

### Peilbuizen (BRO)
`VKPEILBUIZEN` tekent de peilbuizen (grondwatermonitoringputten) uit de Basisregistratie Ondergrond (BRO) in het
gebied, met per filter de grondwaterstanden die de BRO van dat filter heeft. Het palet zet ze onder
**Grondonderzoek**, naast de sonderingen en boringen.
- **Waar het vandaan komt**: VLEA zoekt de putten, hun filters en hun meetreeksen in de kengegevens van de BRO bij
  PDOK (dezelfde dienst als het portaal van VLEA) en haalt daarna van elke meetreeks de metingen bij de BRO zelf
  (`publiek.broservices.nl`). Een put met meer filters (buizen) heeft per filter een eigen reeks; een filter kan ook
  meer reeksen hebben (bijvoorbeeld een oude en een nieuwe), die tellen dan samen.
- **Hoeveel peilbuizen** (optie `aantal`): net als bij de sonderingen en boringen hoogstens **25**, de 25 het dichtst
  bij het midden van het gebied (bij een strook van `VKCONTOUR`: bij de lijn), met dezelfde keuzes (5, 10, 25, 50,
  100 of alle); bij gelijke afstand de diepste eerst. Ook een peilbuis zonder metingen in de BRO staat erop: een buis
  in de grond, tot de diepte van het filter. Wil je alleen peilbuizen met metingen, zet dan de optie `zonderstanden`
  uit.
- **Verwijderde peilbuizen**: een put die volgens de BRO verwijderd is, staat er ook op, want zijn oude standen zeggen
  iets over het grondwater. De buis staat er dan niet meer: het label zegt het direct onder het BRO-id
  (`verwijderd 2021`), `VKINFO` geeft de datum, en de melding zegt hoeveel van de getekende peilbuizen verwijderd zijn.
  In een stadscentrum kan dat de helft zijn (op 09-10-2026 in het centrum van Rotterdam 16 van de 25 dichtstbijzijnde).
  Een put die de BRO uit de registratie heeft gehaald, staat er niet op (zoals bij de sonderingen en boringen); de
  melding noemt hoeveel.
- Elke gekozen peilbuis komt als symbool (twee cirkels, van 1,6 m en 0,6 m doorsnede, blok `VK_PEILBUIS`) op
  `B-WE-MO-ONDERZOEK_PEILBUIS-S` (kleur 150), met rechts ervan een label op `B-WE-MO-ONDERZOEK_PEILBUIS-T35` (kleur
  50, zoals NLCS teksten kleurt) (optie `labels`):

  ```text
  GMW000000009478
  mv +3,42 m NAP
  filter +0,23 tot -0,77 m NAP
  GW gem. +0,87 m NAP (2022-2026)
  hoogst +1,19 (2026), laagst +0,32 (2023)
  laatst +1,04 (12-09-2026)
  ```

  Het BRO-id van de put (bij een verwijderde put met de regel `verwijderd` en het jaar eronder), het maaiveld, en per
  filter de boven- en onderkant van het filter, het gemiddelde van de
  gemeten standen met de jaren, de hoogste en de laagste gemeten stand met het jaar, en de laatste meting met de
  datum. Alles in meters t.o.v. NAP, zoals de BRO het levert. Een put met meer filters noemt het buisnummer
  (`buis 2: filter ...`). Was er op één dag gemeten, dan is het één regel (`GW +0,40 m NAP (03-07-2019)`). Staan
  er meer peilbuizen op (bijna) dezelfde plek, dan komen hun labels onder elkaar.
- **Wat meetelt**: alleen de gewone metingen van de reeks (geen controlemetingen met de hand), niet de metingen die
  de bronhouder heeft afgekeurd of als onbeslist heeft gemarkeerd, en niet een meting zonder stand (bijvoorbeeld een
  droge buis of water boven de bovenkant van de buis). Wel de recente metingen die nog niet zijn beoordeeld, en de oude
  metingen uit het archief van TNO. Is een dag zowel voorlopig als beoordeeld geleverd, dan telt de beoordeelde. Het
  gemiddelde is het gemiddelde van de daggemiddelden: een periode met een meting per uur weegt niet zwaarder dan een
  periode met een meting per twee weken.
- **Geen GHG of GLG**: de BRO levert die niet, alleen de metingen. VLEA rekent ze niet uit, want daarvoor zijn
  acht jaar metingen op vaste dagen nodig en een vaste rekenregel; het label geeft daarom de gemeten uitersten met
  het jaar. Voor een ontwerp: kijk naar de periode en het aantal metingen (`VKINFO`), en naar de filterdiepte (een
  diep filter meet de stijghoogte van een dieper zandpakket, niet de freatische grondwaterstand).
- **Grondwaterstanden** (optie `standen`): uit, dan haalt VLEA niets bij de BRO en noemt het label alleen de jaren
  met metingen volgens de BRO (`metingen 2012-2026 in de BRO`). Hoogstens **50 meetreeksen per keer**, van de
  dichtstbijzijnde peilbuizen eerst; voor de andere noemt het label ook alleen de jaren, en de melding zegt hoeveel.
  Een reeks is 3 kB tot ruim 10 MB (een meting per uur over twintig jaar); voor 25 peilbuizen in een stad is dat samen
  tientallen MB. Gemeten op 9 oktober 2026, de 25 dichtstbijzijnde: Rotterdam 1,5 MB in 7 seconden, Amsterdam 11 MB in
  10 seconden, Groningen 45 MB in 14 seconden, met voortgang en Esc om te stoppen. Lukt een reeks niet, dan zegt de
  melding welke en waarom.
- **Storing bij PDOK**: lukt bij PDOK het zoeken naar de filters of de meetreeksen niet, dan staan de peilbuizen er
  wel, maar weet VLEA niet of de BRO er grondwaterstanden van heeft. Het label zegt dan
  `grondwaterstanden niet opgehaald (PDOK)` (zonder filters: `filter en grondwaterstanden niet opgehaald (PDOK)`), niet
  `geen grondwaterstanden in de BRO`; `VKINFO` zegt `onbekend (niet opgehaald bij PDOK)`, en een waarschuwing zegt
  hoeveel peilbuizen het zijn. Probeer het later opnieuw. Ook met de optie `zonderstanden` uit staan deze peilbuizen
  erop: onbekend is niet hetzelfde als geen metingen.
- De **meetreeksen** zelf komen als CSV van de BRO in de map `<tekening>_kaarten\peilbuizen` naast de tekening
  (optie `csv`; sla de tekening eerst op). Zo kun je de hele reeks zelf bekijken of in een grafiek zetten. De melding
  noemt hoeveel MB het is. `csv` staat standaard aan: in een stad komen er zo tientallen MB naast de tekening, ook op
  een projectschijf. Zet `csv` uit als je de reeksen niet nodig hebt.
- `VKINFO` op een peilbuis geeft per filter (`buis1_...`): filter boven en onder, status, de meetreeksen, het
  gemiddelde, de hoogste, laagste en laatste stand met het tijdstip, de eerste en laatste dag, het aantal metingen
  en dagen, hoeveel regels niet meetellen en de jaren volgens de BRO; voor de put het maaiveld, de putcode, de oude
  code uit het archief van TNO, de datum van inrichting, de functie, de datum van verwijderen (`datum_verwijderd`,
  alleen bij een verwijderde put) en of de BRO de put in onderzoek heeft (`in_onderzoek`, zoals bij de sonderingen en
  boringen).
- De grijze onderlegger laat de peilbuizen in kleur, net als de sonderingen en boringen.
- De peilbuizen zijn informatief: de standen zijn metingen van de bronhouder, niet door VLEA gecontroleerd.
  Controleer periode, filterdiepte en aantal metingen voordat je een stand gebruikt.
- Weghalen: `VKWISSEN`, keuze `Selectie`, het symbool of een regel van het label aanklikken; symbool en label gaan
  samen weg. Alle peilbuizen weg: `VKWISSEN` en dan `peilbuizen`. De CSV-bestanden in de map blijven staan.

Een script, één regel per vraag (het stationsgebied in Amersfoort; daar stonden op 09-10-2026 drie peilbuizen, twee
oude met metingen van 1952 tot 1996 en 2000):

```text
VKPEILBUIZEN
C
153944,462553,154444,463053
aantal=10,vervangen=ja
```

### Wegen en hectometrering (`VKNWB`)
`VKNWB` tekent de wegassen van het Nationaal Wegenbestand op `B-WE-AM-AS_WEG-G` en, met de optie
`hectometrering` (standaard aan), een hectometerpaal op elk hectopunt in het gebied:
- Een **oranje bordje** van 5,1 x 2,7 m op een paal van 1 m, met een cirkeltje op het hectopunt. Op het bordje
  staat boven het wegnummer (`A28`, of een N-weg) en onder de hectometer (`31,7`, met de letter van een parallelbaan
  erachter: `31,6 c`), 0,9 m hoog en in het midden, zoals op het bordje langs de weg en zoals de hectometrering die
  het portaal in de tekening laadt. Heeft de weg geen nummer (bijvoorbeeld een gemeentelijke weg), dan staat alleen
  de hectometer midden op het bordje.
- Het bordje is het blok `VK_HECTOMETERPAAL_BORD` op `B-WE-VW-HECTOMETRERING-S`, met de onzichtbare attributen
  `WEG` en `HM` (handig voor een gegevensextractie). De twee teksten staan op `B-WE-VW-HECTOMETRERING-T18`. Beide
  lagen zijn oranje (kleur 30), een keuze van VLEA: de NLCS-objectentabel geeft het bordje kleur 7 en de tekst
  kleur 10. Wil je die kleuren, zet de lagen dan zo in je sjabloon vóór het laden (zie 7).
- Ligt een hectopunt vlak bij de rand van het gebied, dan steekt het bordje erover; de tekst blijft op het bordje.
- Een hectometerpaal uit een eerdere versie (`VK_HECTOMETERPAAL`, een klein bordje met het label ernaast) blijft
  zoals hij is. Laad opnieuw met Vervangen voor de nieuwe bordjes, en ruim de oude blokdefinitie op met `PURGE`.
  Lagen die al in je tekening staan, houden hun kleur; `VKSTIJL` met de keuze `Nlcs` maakt ze oranje.

### Riolering (`VKRIOOL`)
`VKRIOOL` tekent de riolering die gemeenten aan GWSW leveren (niet elke gemeente doet dat) op de NLCS-lagen voor
riolering: leidingen, putten (blok `VK_RIOOLPUT`), pompen, bouwwerken, lozingspunten en, met de optie `aansluitingen`,
de huisaansluitingen. De laag volgt uit het soort object en het stelsel (gemengd, vuil water, hemelwater …). De
teksten staan allemaal op `B-OI-RI-T18`:
- **Materiaal en diameter** (optie `labels`): boven het midden van de leiding, kort: `PVC Ø315`, `Beton Ø400`,
  `PP Ø300` (polypropyleen), `Gew. beton 2000x1200` (breedte x hoogte bij een niet-ronde buis). Ook PE, HDPE, GVK
  en AC (asbestcement). "Onbekend" en "Anders" laat VLEA weg.
- **Bob** (optie `hoogtes`): de binnenonderkant van de buis in m t.o.v. NAP, onder de lijn, bij het eind waar hij
  geldt: 1 m van de put, de leiding in, `bob -3,23 m NAP`. Op een korte leiding (korter dan ruim 20 m) passen er geen
  twee naast elkaar: dan staat er één label onder het midden met beide waarden, links de bob van het linker eind,
  `bob +1,82 / +1,81 m NAP`. Een eind buiten het gebied krijgt geen bob, en een leiding met bob 0 aan beide kanten
  ook niet: zo vullen sommige gemeenten "onbekend". Niet bij huisaansluitingen: daar is aan de kant van het pand
  geen put, en in een stad zou elke gevel een label krijgen. De bob van een aansluitleiding zie je met `VKINFO`.
- **Putnaam en maaiveld** (ook optie `hoogtes`): naast de put, boven de naam (`150152`) en onder het maaiveld
  (`mv -1,97 m NAP`). Ze staan rechts van de put, of links als daar minder bob- en materiaallabels van de leidingen in
  de weg staan; zo valt de bob van een leiding die naar rechtsboven loopt niet over de putnaam. Bij dichte groepen
  putten en korte leidingen kan een tekst nog over een andere vallen: verschuif hem dan met de hand. Een lange code als
  naam (meer dan 16 tekens) en een maaiveld van precies 0 laat VLEA weg; de onzichtbare attributen `PUT` en `MV` van
  het blok houden de waarden zoals de gemeente ze levert.
- Een put zonder stelsel krijgt het stelsel van de leidingen die erop aansluiten, als dat er één is; heeft geen van die
  leidingen een stelsel, dan telt hun soort (een gemengd riool hoort bij een gemengd stelsel). VLEA meldt hoeveel
  putten zo een stelsel kregen. Lukt het niet, dan staat de put op `B-OI-RI-OVERIG_RIOOLPUT-S` (magenta).
- Nieuwere GWSW-begrippen die de NLCS-tabel voor riolering (5.0) niet kent, zoals een uitlaatconstructie of een
  verbeterd hemelwaterstelsel, krijgen de laag van het begrip dat er het dichtst bij ligt (een HWA-uitlaatconstructie).
  De lijst staat in de laagtabel; staat er toch "objecten zonder laagtoewijzing", meld het dan.

### Het AHN-hoogtemodel (`VKAHN`)
`VKAHN` maakt in Civil 3D van het AHN (Actueel Hoogtebestand Nederland) een hoogtemodel, één per gebied (zie 5). In
AutoCAD zonder Civil 3D staat AHN in het palet grijs; de hoogte op een punt (`VKAHNPUNT`) werkt wel.

**Welke AHN-versie.** VLEA haalt het AHN bij PDOK, en PDOK levert één versie: **AHN4**, ingewonnen in 2020, 2021 en
2022, met pixels van 0,5 m (zo gemeten op 9 oktober 2026). Een versie kiezen kan daarom niet. Nieuwere metingen (AHN5
en AHN6) bestaan wel, maar alleen bij het AHN zelf, voor een deel van het land en niet bij PDOK; VLEA haalt geen
kaarten buiten PDOK (zie 9, Netwerk). Het instellingenvenster zegt het ook, onder **AHN hoogtemodel** en onder **Hoogte
op een punt**. De versie staat in de bronvermelding ("AHN4 DTM 0,5 m"), op de opdrachtregel na het laden en in de
gegevens van het model en van elk hoogtepunt (`VKINFO`: `vk_ahn_versie`). Zet PDOK er ooit een andere versie achter,
dan staat dat in de wijzigingen van een nieuwe versie van VLEA.

De keuzes (tandwiel, **Kaarten**, **AHN hoogtemodel**; getypt bij `VKAHN` als `model=dsm,stap=2`, in `VKLADEN` als
`ahn.model` en `ahn.stap`):
- **Model.** **Maaiveld (DTM 0,5 m)** (`model=dtm`, de standaardkeuze): het terrein, zonder gebouwen en begroeiing;
  onder panden en op water heeft het geen hoogte. **Oppervlak met gebouwen en begroeiing (DSM 0,5 m)** (`model=dsm`):
  de bovenkant van wat er staat, dus geen maaiveld en niet voor een terreinmodel. Het model heet dan "VLEA AHN DSM RD …".
- **Rasterstap**: hoe dicht de punten van het model liggen. **Zo fijn als kan** (`stap=fijnst`, de standaardkeuze): een
  punt per pixel van 0,5 m, bij een groter gebied vanzelf grover, zodat het model onder de 150.000 punten blijft
  (0,25 km²: 1,5 m, 1 km²: 3 m, 4 km²: 5,5 m). **1 m**, **2 m** of **5 m** (`stap=1`, `stap=2`, `stap=5`): een lichter
  model met minder punten, bijvoorbeeld voor een overzicht of een lang tracé. Vraagt het gebied al een grovere stap,
  dan wint die; de opdrachtregel zegt dat dan.
- Bij elke stap is elk punt de hoogte van één echte AHN-pixel, op het midden van die pixel: VLEA middelt en
  interpoleert niets. Het ophalen bij PDOK blijft gelijk (altijd pixels van 0,5 m), dus een grovere stap laadt niet
  sneller; alleen het model wordt lichter.
- Na het laden staat er bijvoorbeeld: "AHN DTM: hoogtemodel 'VLEA AHN RD 154950-462950 100x100' uit AHN4 (ingewonnen
  2020-2022) met 1.260 punten op een raster van 2,0 m." Een tweede model van hetzelfde gebied met een andere stap
  krijgt dezelfde naam; je antwoord op de vraag Vervangen, Erbij of Overslaan beslist (zie 5).

### Tijdens en na het laden
- Tijdens het ophalen zie je per kaart de voortgang (pagina's en objecten; PDOK geeft vooraf geen
  totaal). **Annuleren** of Esc stopt het ophalen binnen enkele seconden; er wordt dan niets half
  getekend. De opdrachtregel zegt waar het werk gebeurt: "Kaart ophalen bij PDOK", "… bij de BRO" of
  "… bij PDOK en Rijkswaterstaat"; bij een KLIC-levering "Levering omzetten en tekenen". Wissel je
  intussen van tekening, dan tekent VLEA niet in de verkeerde.
- Tijdens het ophalen blijft AutoCAD reageren, maar je kunt niet tekenen. Daarna tekent VLEA alles in
  één keer; dan is AutoCAD bezet (geen voortgang). Bij een kaart duurt dat meestal een paar seconden;
  bij een grote KLIC-levering (100.000 objecten of meer) 10 tot 20 seconden en 2 tot 4 GB werkgeheugen
  (gemeten in de AutoCAD-kern). Windows kan dan "reageert niet" tonen: wacht tot het klaar is. Esc
  tijdens het tekenen draait alles terug.
- Staat er na het laden "N objecten zonder laagtoewijzing", dan heeft PDOK een waarde geleverd die
  VLEA nog niet kent. Die objecten staan op een aparte laag (de terugvallaag van die kaart, bij riolering
  `…OVERIG_RIOOLLEIDING-G` of `…OVERIG_RIOOLPUT-S`). Meld het gerust als issue.

### Op de opdrachtregel en in een script
`VKLADEN` zonder palet vraagt achtereenvolgens: het gebied (`Opgeslagen`, `Rechthoek`, `Polylijn` of
`Coördinaten`), de kaarten (sleutels gescheiden door komma's, bijvoorbeeld `bgt`, of `alle` voor alle
kaarten) en de opties (`kaart.optie=waarde`, gescheiden door komma's; Enter = standaard). Er is geen
standaardkaart: typ je bij de kaarten niets, dan noemt VLEA de beschikbare sleutels en laadt niets.
Algemene opties: `vervangen=ja`, `vervangen=erbij`, `vervangen=nee` (zie 5), `stijl=grijs` en
`bronvermelding=uit`. Zonder die opties geldt NLCS, bronvermelding aan en vragen bij een eerdere import,
wat er in de instellingen ook gekozen is. Een script, één regel per vraag:

```text
VKLADEN
C
154750,462750,155250,463250
bgt
bgt.namen=uit,vervangen=ja
```

De kaartcommando's (`VKBGT` enz.) werken ook zonder palet, ook in een script in de AutoCAD-kern
zonder schermen. Ze vragen het gebied en de opties van die ene kaart; Enter bij de opties = de
standaardopties van die kaart. Een script, één regel per vraag:

```text
VKBGT
C
154750,462750,155250,463250
namen=uit,vervangen=ja
```

**Een antwoord dat niet past.** Typ je zelf iets wat bij geen keuze past (`xyz`), of maar een deel van een
sleutel (`bgtb`), dan zegt VLEA dat en stelt dezelfde vraag opnieuw (Esc stopt). In een script gebeurt dat niet:
de herhaalde vraag zou de volgende regel van het script als antwoord nemen en zo bij `VKWISSEN` iets kunnen
wissen. Daar stopt het commando meteen, met één regel die zegt wat er mis was, dat het commando is gestopt en
dat dit antwoord niets heeft gewijzigd. Dat geldt ook voor een lege regel bij een vraag zonder standaard (bij
`VKWISSEN`) en voor AutoLISP (`(command "VKWISSEN" "bgt")`). Een goed antwoord, ook een afkorting zoals `A`,
werkt in een script gewoon. De regels na het gestopte commando worden weer als commando gelezen: staat daar een
commando (`_.QSAVE`), dan loopt dat; staat daar een regel die voor het gestopte commando bedoeld was (een
sleutel, een coördinaat), dan zegt AutoCAD "Unknown command" en stopt het script. Probeer een script dus eerst
op een kopie van je tekening.

### Hoogte op een punt (`VKAHNPUNT`)
Wijs een of meer punten aan (of typ `x,y`); Enter of Esc stopt. Per punt haalt VLEA bij PDOK de
AHN-hoogte van de pixel van 0,5 x 0,5 m waarin het punt valt (geen gemiddelde van buurpixels; AHN4, de enige versie bij
PDOK, zie 4, Het AHN-hoogtemodel) en tekent:

- een punt op die hoogte (z) op de laag `B-WE-OG-HOOGTEPUNT-G`, en
- een label "NAP +4,98 m" rechts van het punt op `B-WE-OG-T18` (0,9 m hoog).

Heeft AHN op die plek geen hoogte (meestal onder een pand of op water), dan komt er alleen het label
"geen AHN-hoogte hier" en géén punt. Werkt ook zonder Civil 3D. Trefwoorden bij de vraag:

| Trefwoord | Keuze | Standaard |
|---|---|---|
| `Model` | `Dtm` (maaiveld) of `Dsm` (met gebouwen en begroeiing; geen maaiveld) | `Dtm` |
| `Label` | `Aan` of `Uit` (alleen het punt) | `Aan` |

Een script, één regel per vraag (de lege regel stopt):

```text
VKAHNPUNT
154910.3,462920.4
154950.25,462950.25

```

### Contour in een script (`VKCONTOUR`)
Trefwoorden bij het kiezen van de lijn: `Breedte` (eerst de breedte, dan volgt er geen breedtevraag
meer) en `Laatste` (het laatst getekende object). Een script:

```text
_.LINE 154800,462950 155000,462950

VKCONTOUR
Breedte
30
Laatste
```

### Punten uit Excel of CSV (`VKPUNTEN`)
Zet punten uit een eigen lijst in de tekening: per rij een punt op zijn hoogte en een leider (multileader) met de
naam en "NAP +1,23 m". Start met de knop **Punten inlezen** in het palet of op het lint, of typ `VKPUNTEN`. Werkt
zonder internet en zonder Civil 3D; het bestand blijft op je eigen pc.

- **Bestanden:** `.xlsx` en `.xlsm` (het eerste zichtbare werkblad; macro's leest VLEA niet), `.csv`, `.txt` en
  `.tsv` (puntkomma, tab, komma, `|` of spaties; UTF-8, of zoals Nederlandse Excel een CSV opslaat). Een oud
  Excel-bestand (`.xls`), een bestand met een wachtwoord, `.xlsb` en `.ods` leest VLEA niet: sla ze op als `.xlsx`
  of `.csv`. Een bestand dat open staat in Excel, leest VLEA zoals het opgeslagen is. Hoogstens 50 MB en 200.000
  rijen.
- **Alleen RD:** X en Y zijn RD-coördinaten en de hoogte is in meters ten opzichte van NAP. VLEA rekent niets om.
  Lengte- en breedtegraden en lokale coördinaten herkent VLEA en zegt dat in een zin.
- **Kolommen:** met een kopregel herkent VLEA de kolommen aan de kop: `Nr`, `X`, `Y`, `NAP`, `Omschrijving`, maar
  ook `x-coördinaat`, `oost`, `noord`, `maaiveld`, `hoogte`, `boring`, `opmerking`, Engelse koppen en de letters
  `P;N;E;Z;C` van een landmeter. Zonder kopregel kijkt VLEA naar de waarden: twee kolommen naast elkaar in het bereik
  van RD zijn X en Y (in welke volgorde ook), de eerstvolgende kolom met getallen tussen -50 en +400 is de hoogte, de
  kolom ervoor de naam en de laatste kolom met tekst de omschrijving. Een kolom `diepte`, `lengte` of `dikte` wordt
  nooit de hoogte. De andere kolommen komen als gegevens bij het punt (`VKINFO`).
- **Wat je ziet:** wat er gelezen is, welke kolom wat is, het eerste punt (met de coördinaten die VLEA las) en het
  bereik van de hoogtes. Komt de indeling (deels) uit de waarden, dan vraagt VLEA eerst **Zijn de kolommen goed?
  [Ja/Kolommen/Annuleren]**, zonder standaard. Daarna: `4 punten tekenen (schaal 1:500, tekst naam en hoogte, met
  leiders), Enter = tekenen [Tekenen/Schaal/Tekst/Leiders/Kolommen/Annuleren]`.

| Trefwoord | Keuze | Standaard |
|---|---|---|
| `Schaal` | de schaal waarop je afdrukt, 1:50 tot 1:5000; de tekst wordt 1,8 mm op papier (0,9 m op 1:500, 0,45 m op 1:250, 0,36 m op 1:200) | 1:500 |
| `Tekst` | `NaamHoogte`, `Naam`, `Hoogte` of `Alles` (ook de omschrijving) | `NaamHoogte` |
| `Leiders` | `Aan`, of `Uit` voor alleen de punten | `Aan` |
| `Kolommen` | zelf kiezen: VLEA toont per kolom het nummer, de kop en twee voorbeelden, vraagt of de eerste rij een kopregel is en per rol het kolomnummer (0 = geen) | |

- **Bij twijfel geen standaard:** lijken X en Y verwisseld, dan vraagt VLEA `Verwisselen`; lijkt de hoogtekolom
  geen meters NAP (bijvoorbeeld centimeters), dan `Negeren` (alle punten op z = 0); staan er decimale komma's én
  punten in het bestand, dan `Komma` of `Punt`.
- **In de tekening:** het punt op `X-XX-AL-REFERENTIE-G`, op zijn hoogte; zonder hoogte op z = 0 (de samenvatting
  zegt hoeveel, `VKINFO` toont dan `vk_geen_hoogte`). Hoe een punt eruitziet, bepalen `PDMODE` en `PDSIZE` van je
  tekening; VLEA verandert die niet. De leider op `X-XX-AL-REFERENTIE-T18` (rood, zoals NLCS), met een gevulde pijl
  op het punt, een korte knik en de tekst op een masker in de kleur van de achtergrond, in de leiderstijl
  `VK_LEIDER_500` (de schaal staat in de naam; staat er al een stijl met die naam, dan blijft die zoals hij is) en
  de tekststijl `VLEA_ISO`. Dezelfde lagen als een KML-import: er is geen laagnaam bijgekomen.
- **Plaatsing:** in de volgorde van het bestand, eerst rechtsboven het punt, en verder weg of in een andere richting
  als de tekst anders een andere tekst of een ander punt uit het bestand raakt. Lukt dat niet, dan staat de leider
  rechtsboven en zegt de samenvatting hoeveel leiders niet vrij staan; verschuif ze met de grip. VLEA kijkt alleen
  naar de punten uit het bestand, niet naar de kaart eronder.
- **Overgeslagen:** een rij zonder bruikbare X of Y, of buiten RD, slaat VLEA over; een hoogte buiten -50 tot +400 m
  wordt "geen hoogte". VLEA noemt het aantal en de eerste tien regelnummers (bij Excel het rijnummer dat Excel
  toont). Bij meer dan 1.000 punten stelt VLEA voor alleen de punten te tekenen (Enter = ja); meer dan 50.000 punten
  tekent VLEA niet in één keer.
- **Opnieuw inlezen:** lees je hetzelfde bestand (dezelfde naam) nog eens in, dan vraagt VLEA
  **[Vervangen/Erbij/Overslaan]**. Enter = Vervangen: de punten en leiders van de vorige keer gaan weg, ook wat je
  er zelf aan veranderde (zoals een verschoven leider). Een ander bestand wordt nooit gewist. Wissen en tekenen
  gaan in één keer: `U` maakt alles ongedaan, en Esc tijdens het tekenen ook.
- `VKWISSEN` met de sleutel `punten` wist alle ingelezen punten met hun leiders; met `Selectie` gaat een punt met zijn
  leider weg. `VKINFO` toont bij punt en leider het bestand, de rij, naam, omschrijving, hoogte en de andere kolommen.
- `VKKMZ` neemt het punt mee naar Google Earth (met bron en rij), de leider niet.

Een script met `FILEDIA` op 0 (een lege regel is Enter). Komt de indeling uit de waarden, zet dan `Ja` op de regel
na het pad:

```text
FILEDIA 0
VKPUNTEN
"C:\Werk\punten.csv"

FILEDIA 1
```

### NAP-hoogte in een lengteprofiel (`VKNAPSET`, `VKNAPLEADER`, `VKNAPUPDATE`)
Zet in een lengteprofiel bij een aangewezen punt een leider met de NAP-hoogte. VLEA rekent die hoogte uit met een
referentie: een punt op een lijn waarvan je de hoogte weet, en de verticale schaal van het profiel. Dit doet wat het
LISP-script NAPLEADER deed. Werkt zonder internet en zonder Civil 3D; VLEA haalt niets op.

1. **NAP-referentie** (`VKNAPSET`, eenmaal per tekening of na een andere schaal): wijs het punt aan op de lijn met de
   bekende hoogte (of typ `x,y`), typ de NAP-hoogte van dat punt in meters en het aantal tekeneenheden per
   hoogtemeter (de verticale schaal, groter dan 0). Enter = de waarde van de vorige referentie (de eerste keer 0 en
   1). Er komt een liggend driehoekje met de punt op het aangewezen punt en daarnaast "NAP-REFERENTIE" en de hoogte,
   bijvoorbeeld "NAP +1,25 m". Trefwoord bij het aanwijzen: `Teksthoogte` (de hoogte van symbool en teksten in
   tekeneenheden, standaard 0,5; hij geldt voor alle leiders die je daarna zet). Een vorige referentie, ook die van
   het LISP-script, wordt vervangen, pas nadat de nieuwe er staat. Staan er in dezelfde ruimte al leiders, dan
   vraagt VLEA **Hier staan al 3 NAP-leiders. Herberekenen met de nieuwe referentie [Ja/Nee] <Ja>**: met `Ja`
   rekenen ze met de nieuwe referentie, met `Nee` houden ze die van toen ze getekend werden.
2. **NAP-leider** (`VKNAPLEADER`): wijs het punt aan waarvan je de hoogte wilt weten. De opdrachtregel noemt de
   hoogte, bijvoorbeeld "NAP +3,50 m. Wijs de plek van de tekst aan"; wijs die plek aan. Er komt een leider met een
   pijl op het punt en de tekst in een kader met een masker. Dat herhaalt tot Enter; Enter bij de plek van de tekst
   slaat dat ene punt over. Daarna "3 NAP-leiders geplaatst." De hele reeks is één keer `U`. Is er nog geen referentie
   in de tekening, dan begint VLEA met stap 1.
3. **NAP herberekenen** (`VKNAPUPDATE`): heb je een leider verschoven, dan klopt zijn tekst pas weer na herberekenen:
   "NAP-leiders: 2 herberekend, 5 ongewijzigd." Elk NAP-commando rekent aan het eind ook de andere leiders na en zegt
   het als er een veranderd is. Anders dan het LISP-script werkt een leider zich niet vanzelf bij na verschuiven.

- **De berekening:** NAP = de hoogte van de referentie + (Y van het punt - Y van de referentie) / de verticale schaal.
  VLEA rekent met de Y van het wereldstelsel, net als het LISP-script. Is het UCS gedraaid, dan zegt VLEA dat; zet het
  UCS dan op Wereld (`UCS`, Enter). Elke leider bewaart de referentie waarmee hij getekend is (zie `VKINFO`), zodat
  leiders van een ander profiel hun eigen hoogte houden.
- **Eenheid en plek:** de eenheid van de tekening doet er niet toe, alleen de verticale schaal die je opgeeft; een
  tekening in millimeters krijgt één regel uitleg. RD speelt geen rol. De referentie hoort bij de ruimte waarin hij
  staat: de modelruimte of de papierruimte van een layout. Werk je in een andere ruimte, dan zegt VLEA waar de
  referentie staat; stel daar zo nodig een nieuwe in.
- **In de tekening:** symbool en tekst op `HDD-NAP-REFERENTIE` (kleur 7), de leiders op `HDD-NAP-LEADER` (kleur 1,
  rood), allebei 0,25 mm: dezelfde lagen als het LISP-script, dus je laagfilters en plotstijlen blijven kloppen. Een
  bestaande laag blijft zoals hij is; staat hij uit of bevroren, dan zegt VLEA dat de leider er wel staat maar niet te
  zien is. Tekst in de tekststijl `VLEA_ISO`, leiders in de leiderstijl `VK_LEIDER_NAP` (een bestaande stijl met die
  naam blijft zoals hij is; pijl, knik, kader en masker zet VLEA per leider). Kleur, lijntype en lijndikte
  DOORLAAG.
- **Tekeningen met het LISP-script:** VLEA leest de referentie en de leiders van het script en rekent ermee; de
  opdrachtregel zegt dat. **NAP herberekenen**, en **NAP-referentie** met `Ja`, nemen de leiders van het script over:
  daarna houdt alleen VLEA ze bij en heeft de tekst een komma ("NAP +1,25 m"; het script schreef "NAP +1.25 m"). Een
  gewoon NAP-commando neemt niets over; het zegt alleen hoeveel leiders nog van het script zijn. Haal het script na
  het overnemen uit je opstartset (`APPLOAD`), zodat er niet twee systemen naast elkaar werken.
- Een leider met meer dan één leiderlijn, of zonder gewone tekst, rekent VLEA niet na; de melding zegt hoeveel.
- `VKWISSEN` kent de sleutels `nap-referentie` en `nap-leader`; `VKINFO` toont bij een leider de referentie, de
  verticale schaal en de laatst berekende hoogte. `VKKMZ` neemt de leiders niet mee naar Google Earth.

Een script (getallen met een punt, een lege regel is Enter). Staan er al leiders, dan vraagt `VKNAPSET` of ze
herberekend worden: zet dan `Ja` of `Nee` op de regel na de verticale schaal.

```text
VKNAPSET
10,50
1.25
10
VKNAPLEADER
60,70
65,75

VKNAPUPDATE
```

### Maatlijnen langs een lijn (`VKMAAT`)
Zet bij elk stuk van een lijn of polylijn een maat: de rechte afstand tussen de twee hoekpunten, op een maatlijn
2 m van dat stuk. Dit doet wat het LISP-script VERTEXMAAT deed, met een paar verschillen (hieronder). Typ `VKMAAT`;
er is geen knop in het palet. Werkt zonder internet.

- **Kiezen:** "Kies een lijn of polylijn voor maatlijnen op 2 m (open lijn: rechts van de tekenrichting)
  [Afstand/Kant/Laatste]". Eén klik op de lijn is genoeg. Een lijn, een polylijn (ook met bogen) en een oudere 2D- of
  3D-polylijn kan VLEA bematen; een afgevlakte polylijn (spline of passende kromme), een boog, cirkel of spline niet:
  dan zegt VLEA waarom en vraagt opnieuw.
- **Meer lijnen tegelijk:** kies ze eerst (bijvoorbeeld met een venster) en typ dan `VKMAAT`. Alle lijnen en
  polylijnen in die keuze krijgen maten, zonder vraag; andere objecten slaat VLEA over en telt het.
- **Trefwoorden:** `Afstand` (van de maatlijn tot de lijn, 0,1 tot 100 m; typen of twee punten aanwijzen),
  `Kant` (bij een open lijn `Rechts` of `Links` van de tekenrichting, standaard rechts) en `Laatste` (het laatst
  getekende object, handig in een script).
- **Gesloten polylijn:** de maten staan altijd buiten de vorm, ook bij een inspringende hoek (een L-vorm). Een
  polylijn waarvan het laatste punt op het eerste ligt, telt ook als gesloten. Een gesloten lijn zonder oppervlak
  (heen en terug over dezelfde lijn) bemaat VLEA niet; een lijn die zichzelf kruist wel, met een melding.
- **Bogen:** de maat is de rechte afstand tussen de twee hoekpunten (de koorde), niet de lengte van de boog. Steekt
  de boog naar de kant van de maat uit, dan komt de maatlijn 2 m buiten de boog. De melding zegt hoeveel stukken een
  boog waren.
- **In de tekening:** uitgelijnde maten op de laag `X-XX-AL-REFERENTIE-M` (kleur 7, 0,18 mm) met de maatstijl
  `VK_MAAT`: tekst 1,0 m (2 mm op papier bij 1:500) boven de maatlijn en meelopend, met een masker zodat kaartlijnen
  niet door de cijfers lopen; twee decimalen met een komma ("12,35"); pijlen van 1,0 m; kleur, dikte en lijntype van de
  laag. Je actieve maatstijl en je eigen maatinstellingen blijven zoals ze waren. Een bestaande laag of maatstijl met
  die naam blijft zoals hij is: pas je `VK_MAAT` aan, dan volgen de nieuwe maten jouw stijl.
- **Daarna:** "Maatlijnen: 8 getekend op 2 m van de lijn (…). Terugdraaien: U; alle maatlijnen wissen: VKWISSEN,
  maat." `U` haalt alles van die keer weg. Eén maat weghalen gaat gewoon met Delete. De maten zijn niet gekoppeld aan
  de lijn: verplaats je de lijn, dan blijven de maten staan. Twee keer `VKMAAT` op dezelfde lijn geeft de maten dubbel.
- Stukken korter dan 5 mm (ook een dubbel punt) krijgen geen maat; de melding zegt hoeveel. Hoogstens 500 maten per
  keer: bij meer tekent VLEA niets en zegt het dat.
- Alleen in een tekening in meters, en alleen voor lijnen in de modelruimte. De maat staat op z = 0.
- `VKINFO` op een maat toont de lijn, het stuk, de lengte, de afstand en of het een boog was.
- **Verschil met het LISP-script:** de maten komen op de vaste laag `X-XX-AL-REFERENTIE-M` in de stijl `VK_MAAT` (het
  script tekende op de huidige laag met de huidige maatstijl); bij een L-vorm of een scheve vorm staan ze nu buiten,
  op precies 2 m (het script zette ze vanuit het gemiddelde van de hoekpunten, soms binnen de vorm); bij een open
  lijn kun je de kant kiezen; een boog wordt gemeld. Afstand, tekst, pijlen en hulplijnen zijn dezelfde.

Een script dat de laatst getekende lijn bemaat, op 3 m en bij een open lijn links (getallen met een punt):

```text
VKMAAT
Afstand
3
Kant
Links
Laatste
```

## 5. Opnieuw laden en wissen
- Laad je een kaart in een gebied waar die kaart al (deels) staat, dan vraagt VLEA op de
  opdrachtregel **[Vervangen/Erbij/Overslaan]**, ook als je vanuit het palet laadt:
  - **Vervangen** wist de eerdere import(s) van die kaart die het gebied raken, en laadt opnieuw.
    Overlapt een eerdere import maar gedeeltelijk, dan verdwijnt die import helemaal, ook het deel
    buiten het nieuwe gebied; de vraag zegt dat erbij.
  - **Erbij** laadt zonder iets te wissen; waar de gebieden overlappen, staan objecten dan dubbel.
  - **Overslaan** laadt die kaart niet.
  - Enter kiest **Vervangen** als het nieuwe gebied de eerdere import(s) helemaal omvat (hetzelfde of
    een groter gebied). Bij een gedeeltelijke overlap is er geen standaard: kies zelf. Is je nieuwe
    gebied een polygoon, dan kan VLEA niet zeker zeggen dat het de eerdere import omvat en is er ook
    geen standaard.
  - Een eerdere import in een gebied dat het nieuwe niet raakt (ook: alleen een rand gemeen), blijft
    staan; dan vraagt VLEA niets.
  - **Let op:** wijzigingen die je zelf aan gewiste objecten hebt gedaan, verdwijnen. AHN DTM en DSM
    zijn één kaart: laad je DSM waar al een DTM-model staat, kies dan **Erbij**.
  - Ligt er in het nieuwe gebied niets meer van die kaart (PDOK levert niets en er ging niets mis), dan
    wist **Vervangen** de eerdere import en tekent niets: de tekening toont dan de actuele stand. Is er
    niets opgehaald (alle onderdelen van de kaart staan uit, de tekening heeft nog geen map voor de
    beelden, of het ophalen mislukte), dan wist VLEA niets: de eerdere import blijft staan en de
    opdrachtregel zegt dat.
  - In een script: `vervangen=ja` (vervangen), `vervangen=erbij`, `vervangen=nee` (overslaan) of
    `vervangen=vragen`.
  - Bij een KLIC-levering gaat dit per meldnummer, niet per plek: een andere levering wordt nooit
    gewist (zie 6).
- `VKWISSEN` wist eigen imports, per kaart te kiezen (of `Alle`). Andere objecten in de tekening blijven
  staan. Hoogtepunten staan erin als `ahn-punt`, contouren als `contour`, punten uit een bestand (`VKPUNTEN`) als
  `punten`, het NAP-gereedschap als `nap-referentie` en `nap-leader`, en maatlijnen (`VKMAAT`) als `maat`.
  - Typ de sleutel van een kaart voluit, ook als hij het begin is van een andere (`bgt` naast `bgtbeeld`,
    `ahn` naast `ahn-punt`); hoofdletters maken niet uit. Alleen `Alle` en `Selectie` mag je afkorten, tot `A`
    en `S`, zoals overal in AutoCAD. Een losse `s` is daarom altijd Selectie, ook als `sonderingen` of `spoor`
    in de tekening staat. Past wat je typt bij geen keuze, of is het maar een deel van een sleutel (`bgtb`),
    dan zegt VLEA dat en stelt dezelfde vraag opnieuw. Staat zo'n antwoord in een script, dan stopt `VKWISSEN`
    meteen en wist niets (zie 4): de volgende regel van het script wordt weer als commando gelezen.
- **Een deel wissen: `VKWISSEN`, keuze `Selectie`.** Kies de objecten die weg moeten (aanklikken, of een
  venster trekken) en druk op Enter. VLEA wist wat bij een gekozen object hoort: van een sondering het
  symbool, de labelregels en de hele sondeerplot; van een vlak de arcering en de randen. De opdrachtregel
  zegt daarna per kaart wat er weg is.
  - Een label hoort bij zijn object: klik je het label aan, dan gaat het object mee. Een huisnummer van de
    BGT neemt het pand mee (met zijn andere huisnummers), een huisnummer van de BAG het adrespunt, het label
    van een rioolleiding die leiding, een tekst op een hectometerbordje het hele bordje (de paal en beide
    teksten). Van een straatnaam gaan
    alle plekken waar die naam staat samen weg. Een perceelnummer en een kilometertekst van het spoor staan
    op zichzelf. Wil je alleen een tekst weg, gebruik dan het gewone `ERASE` van AutoCAD: dat haalt alleen
    weg wat je aanwijst.
  - Het geldt voor alles wat VLEA tekende, behalve een KLIC-levering. Trek je een venster over een stuk
    tekening, dan gaat dus ook de BGT of het kadaster mee dat daar ligt; klik liever de objecten zelf aan
    als er andere kaarten onder liggen.
  - Objecten die VLEA niet tekende, blijven staan; de melding zegt hoeveel.
  - Een KLIC-levering wis je alleen als geheel (`VKWISSEN`, sleutel `klic`): gekozen KLIC-objecten blijven
    staan, en de melding zegt dat.
  - Wat bij elkaar hoort, leest VLEA uit het id bij de bron (`VKINFO` toont het). Spoor, riolering of zones
    langs waterkeringen die met 0.2.2 of eerder zijn geladen, hebben nog id's die twee objecten kunnen delen
    (bij het spoor het tracé en de kilometrering, bij de riolering op de grens van twee gemeenten, bij de
    zones de kernzone en de beschermingszone van enkele waterkeringen van Rijkswaterstaat): laad die kaart eerst
    opnieuw (Vervangen). De opdrachtregel zegt altijd hoeveel objecten er weg zijn.
  - Wat je zelf aan die objecten veranderde, gaat mee weg, net als bij Vervangen.
  - Blijft van een import alleen de bronvermelding over, dan gaat die tekst mee; staat er van een kaart
    niets meer, dan verdwijnt ook de bronvermelding uit de tekeningeigenschappen.
  - Bij een sondering met een sondeerplot blijft de plek in de rij plots leeg; de andere plots en hun
    volgnummers blijven zoals ze waren (zie 4, Sonderingen weghalen).
  - Enter zonder iets te kiezen wist niets. `U` maakt het wissen ongedaan.
  - In een script, één regel per vraag: `VKWISSEN`, `Selectie`, dan de keuze zoals bij elk AutoCAD-commando
    (bijvoorbeeld `W` met twee hoekpunten) en een lege regel. Geprobeerd in de AutoCAD-kern zonder schermen,
    met `W`, `C`, `F`, `L` en `ALL`.
- Een kopie die je zelf van een VLEA-object maakte (bijvoorbeeld met `COPY`), telt als hetzelfde object: ze
  draagt hetzelfde kenmerk en gaat dus mee bij Selectie, bij Vervangen en bij wissen per kaart.
- **Beelden** (de luchtfoto, de BRT als plaatje en de BGT als kaartbeeld): wis je een beeld (per kaart, met
  Selectie of met Vervangen), dan gaat ook de koppeling naar het beeldbestand weg, de rij in het palet External
  References (`XREF`). Gebruikt een ander beeld hetzelfde bestand nog, bijvoorbeeld een beeld dat je zelf met dat
  bestand invoegde of een beeld in een blok, dan blijft de koppeling staan.
  - Het bestand zelf blijft staan in de map `<tekening>_kaarten`: `U` direct na het wissen zet het beeld meteen
    terug, en een andere tekening kan dezelfde map gebruiken. Gebruikt geen tekening de beelden nog, ruim die map
    dan zelf op.
  - Wiste je beelden met 0.2.3 of eerder, dan staan hun koppelingen nog in External References, zonder beeld in de
    tekening (zie 12).
- `VKINFO` toont bij een object waar het vandaan komt (bron, id, datum) en de gegevens van PDOK, ook
  bij het AHN-model in Civil 3D. Wissen of vervangen van dat model haalt het uit profielen die erop
  gebaseerd zijn; koppel ze daarna opnieuw.
- Elk AHN-gebied wordt een eigen hoogtemodel, met het gebied in de naam: "VLEA AHN RD
  154750-462750 500x500" is het gebied met linksonder RD 154750, 462750 en 500 x 500 m (DSM: "VLEA
  AHN DSM RD …"). Een hoogtemodel van een gebied dat het nieuwe niet raakt, blijft altijd staan en
  wordt nooit hernoemd; bij hetzelfde of een overlappend gebied beslist je antwoord op de vraag
  hierboven. Bestaat de naam al (bijvoorbeeld na **Erbij**), dan krijgt het nieuwe model een
  volgnummer: "… (2)".

## 6. Een KLIC-levering tekenen (`VKKLIC`)
Een KLIC-melding doe je zelf bij het Kadaster; VLEA tekent de levering die je terugkrijgt. Daar is
geen internet voor nodig en er gaat niets van de levering naar buiten. Start met de knop
**KLIC-levering** in het palet of **KLIC** op het lint (de opties komen dan uit de instellingen), of
typ `VKKLIC`. Vanuit palet en lint komt een levering altijd in NLCS-kleuren, ook als je in de
instellingen "grijze onderlegger" voor de kaarten gekozen hebt; grijs kan daarna met `VKSTIJL`, of
getypt met `stijl=grijs`.

**Vertrouwelijk.** Een KLIC-levering is vertrouwelijk (WIBON art. 4 lid 2): je mag de gegevens, ook in
een tekening of een Google Earth-bestand, alleen aan anderen geven voor zover dat noodzakelijk is om
graafschade te voorkomen, of voor de oriëntatie op een verzoek tot medegebruik of coördinatie. De
bronvermelding zegt daarom "(WIBON, vertrouwelijk)", en `VKKMZ` neemt KLIC met Enter niet mee (zie 10).

1. **Bestand kiezen.** Kies de zip die je van het Kadaster kreeg, of uit de uitgepakte levering de
   XML `GI_gebiedsinformatielevering_….xml`. Een zip in een zip mag ook. Staat `FILEDIA` op 0 (of
   draai je een script), dan vraagt VLEA het pad op de opdrachtregel: typ het volledige pad met `.zip`
   of `.xml` (tussen aanhalingstekens als er een spatie in staat), of typ `~` om toch het venster te
   krijgen. Blijft het venster altijd weg, zet dan `FILEDIA` op 1 (na een afgebroken script staat hij
   soms nog op 0). Kies je een ander bestand of een map, dan zegt VLEA dat meteen, vóór de vraag naar
   de opties.
2. **Opties.** Enter = de standaard: maatvoering en annotaties uit, de rest aan (zie de tabel). Iets aan- of
   uitzetten: bijvoorbeeld `maatvoering=aan,annotatie=aan` (alles zoals tot en met 0.2.3) of `diepte=uit`. De
   algemene opties werken zoals bij de kaarten: `vervangen=ja|erbij|nee`, `stijl=grijs` en
   `bronvermelding=uit`.
3. **Inlezen en tekenen.** VLEA leest de levering (voortgang; Esc stopt) en tekent hem op zijn eigen
   plek in RD. Je kiest geen gebied: de levering bepaalt waar hij komt.

| Optie (sleutel) | Wat | Standaard |
|---|---|---|
| `maatvoering` | maatlijnen en maten van de netbeheerder | uit |
| `annotatie` | labels en verwijslijnen van de netbeheerder | uit |
| `diepte` | dieptes t.o.v. maaiveld en NAP, als label | aan |
| `eigentopografie` | eigen topografie van de netbeheerders | aan |
| `detailinfo` | plekken met extra detailinformatie (profielschets, aansluiting) | aan |

Kabels en leidingen, mantelbuizen, putten, kasten en andere netobjecten, zones met een eis
voorzorgsmaatregel en het aanvraaggebied tekent VLEA altijd; dat is geen optie.

Maatvoering en annotaties staan standaard uit: in een gewone levering zijn de maatlijnen, pijlen, maten en
labels van de netbeheerders samen meer dan de helft van wat er getekend wordt, en de kabels en leidingen
verdwijnen erin. Ze staan wel in de levering. Wil je ze in de tekening, zet dan in de instellingen (Gereedschap,
KLIC-levering) het vinkje **Maatvoering** of **Annotaties** aan, of typ `maatvoering=aan,annotatie=aan`. Wat er
door een optie niet getekend is, staat op de opdrachtregel ("Uitgezet (maatvoering=uit): 2.100 objecten; …") en in
de verantwoording in de tekening ("Uitgezet, wel in de levering: maatvoering 2.100, annotatie 900.").

**Wat je daarna ziet**
- Op de opdrachtregel: hoeveel objecten er in de levering staan, per thema hoeveel
  er getekend zijn, en elk object dat niet getekend kon worden, met de reden; kabels en leidingen
  eerst, hoogstens 200 (daarna "... en nog N (per soort geteld in het logboek)"). Het logboek telt ze
  allemaal per soort (klasse, thema en reden, zonder id). Een thema dat VLEA niet kent, staat bij zijn
  naam uit de levering ("thema …"); "thema onbekend" betekent dat het net van het object niet in de
  levering staat, of dat het net geen thema heeft. Heeft een net geen thema, dan neemt VLEA het thema van het
  soort net als dat maar één thema kan zijn (telecommunicatie wordt datatransport, water water, warmte warmte) en
  zegt dat in een melding. Bij elektriciteit (laag-, midden- of hoogspanning?), olie, gas en chemie, en riool
  doet VLEA dat niet: die objecten staan op de lagen van overig, de melding noemt het soort net, en `VKINFO` toont
  het bij het object. Kijk dan in de levering welk net het is.
  Staan er kabels of leidingen in de levering maar is er geen enkele te tekenen (bijvoorbeeld in een
  ander coördinatenstelsel), dan zegt de eerste regel dat, als waarschuwing.
- **Eis voorzorgsmaatregel:** heeft de levering zones met een eis voorzorgsmaatregel, bijlagen met de
  eis, of kondigt een netbeheerder een eis aan zonder zone, dan staat er een waarschuwing met het aantal
  zones per thema en het aantal bijlagen, en de zin "Lees vóór graafwerk de eis en de bijlage(n) in de
  levering en neem contact op met de netbeheerder." Bij elke zone staat in de tekening "Eis
  voorzorgsmaatregel (thema): …" met de eis zoals de netbeheerder hem levert (een heel lange eis
  ingekort; de hele eis staat bij `VKINFO`), ook als de zone een lijn of een punt is.
- **Bijlagen:** een regel met de bijlagen die de levering noemt, per soort (algemeen, bij een eis
  voorzorgsmaatregel) en de plekken met detailinformatie per soort (profielschets, aansluiting …).
- **Status en ligging:** staan er geplande, in aanleg zijnde, buiten gebruik of buiten dienst gestelde
  objecten in de levering, of kabels en leidingen op of boven maaiveld, dan noemt een melding de
  aantallen. VLEA tekent ze op dezelfde lagen als bestaande, ondergrondse kabels en leidingen; de status
  en ligging per object staan bij `VKINFO`, in het Nederlands met de code uit de levering erachter
  ("Status: gepland (projected)", "Ligging: opgehangen of verhoogd (suspendedOrElevated)").
- **Standaard aanlegdiepte:** geeft de netbeheerder voor een net een standaard aanlegdiepte, dan staat
  die bij `VKINFO` van de kabels, leidingen en andere netobjecten van dat net ("0,60 m-mv (standaard,
  niet gemeten)"). Het is geen meting en komt nooit als label in de tekening.
- Kon AutoCAD een deel van de tekenobjecten niet tekenen, dan staat boven de verantwoording "LET OP: N
  tekenobjecten konden niet getekend worden; de levering staat dus niet volledig op de tekening". De
  opdrachtregel en het logboek zeggen meer.
- In de tekening, linksboven de levering, een verantwoording: meldnummer, soort melding en datum, de
  telling ("Volledigheid: 1.234 objecten in de levering = … getekend + … niet te tekenen + …
  uitgezet + … administratief (niet getekend)."), de regel over de eis voorzorgsmaatregel, per thema
  hoeveel er getekend is (samen precies het aantal getekend, met de objecten zonder thema erbij, zoals
  het aanvraaggebied), bij niet-getekende objecten waar de reden staat (per object op de opdrachtregel,
  per soort in het logboek), wat een optie uitzette ("Uitgezet, wel in de levering: …"), de regel over de
  bijlagen en de zin "Informatief; de levering zelf blijft leidend bij graafwerk." De bronvermelding onder de levering en in de tekeningeigenschappen noemt
  dezelfde zin.
- **Administratief** zijn de gegevens van de levering zelf, de netbeheerders en belanghebbenden, de
  bijlagen, en de netten en netdelen waaruit VLEA de kabels en leidingen samenstelt. Die horen niet
  als object in een tekening. De contactvelden uit de levering (contactpersoon, naam, telefoon, e-mail,
  adres, aanvrager) neemt VLEA niet over; een e-mailadres in een vrij tekstveld wordt weggelaten. Wat
  een netbeheerder in een vrije tekst of een label zet, komt verder ongewijzigd mee (alleen een paar tekens die
  het lettertype niet kent, worden in de tekening een gewoon teken; zie 7. Lagen en stijl).
- **Niet te tekenen** is bijvoorbeeld een kabel waarvan geen enkel deel in de levering zit (hij ligt
  buiten het leveringsgebied), een object in een ander coördinatenstelsel dan RD, of een label zonder
  tekst. Loopt een kabel maar deels buiten het gebied, dan staat het deel binnen het gebied er wel.

**Lagen.** Per thema tekent VLEA op een vaste set NLCS-lagen (discipline OI), bijvoorbeeld voor
laagspanning `B-OI-KL-ET_LS-G` (kabels), `…-ET_LS_MANTELBUIS-G` (mantelbuizen, kabelgoten en kabelbedden),
symbolen op `-S`, teksten op `-T18` en maatvoering op `-M`. Een kabelbed is een band op de mantelbuislaag, net als
een mantelbuis of kabelgoot (tot en met 0.2.3 een kabel op de kabellaag); `VKINFO` toont bij elke band de klasse
uit de levering (`Kabelbed`, `Duct` of `Mantelbuis`). Riool vrij verval volgt het stelsel (gemengd, vuil
water, hemelwater). Op de lagen van kabels, leidingen en mantelbuizen loopt het lijntype door over de hoekpunten
(lijntypegeneratie aan per polylijn): ook een kabel met veel korte stukken krijgt zijn streepjes en letters. Wil
je dat voor een polylijn niet, zet het dan uit met `PEDIT` (optie Ltype gen) of in het eigenschappenvenster.

**Symbolen.** Een put, kast, mast, toren, technisch gebouw of leidingelement wordt een blok op de symboollaag
(`-S`) van zijn thema, met de draaiing uit de levering. Welk symbool het wordt, hangt af van de klasse, bij een
leidingelement van de soort (`appurtenanceType`) en daarna van het thema. Staat de soort niet in de lijst, dan kijkt
VLEA nog of "brandkraan" of "lichtmast" in het label staat; anders is het een cirkel. De bloknaam is de naam uit de NLCS
5.02-symbooltabel met `VK_` ervoor (`VK_` staat voor elk blok van VLEA: een blok onder dezelfde naam van andere
software in je tekening zou AutoCAD anders gebruiken in plaats van dat van VLEA). Heeft NLCS voor die soort in dat thema
geen naam, dan heet het blok `VK_KLIC_…`. De vormen zijn van VLEA zelf. Elk blok heeft de onzichtbare attributen
TYPE (de soort uit de levering, bij een put, kast, mast, toren of technisch gebouw de klasse), LABEL en OMSCHRIJVING
(van de netbeheerder; leeg als de levering ze niet heeft). Je ziet ze met `ATTDISP`, `EATTEDIT` of een
gegevensextractie. Grootte: de meeste symbolen 0,20 m (zoals in het portaal; nooit kleiner), een put 0,225 m, een kast
0,40 x 0,20 m, een technisch gebouw en een hoogspanningsmast 0,40 m, een brandkraan 0,50 x 0,27 m.

In de lijst is elektra laag-, midden- en hoogspanning en het landelijk hoogspanningsnet; "andere leidingen" zijn gas,
water, warmte, petrochemie, gevaarlijke inhoud, overig, wees en een thema dat VLEA niet kent.

| Symbool (soort in de levering) | Vorm | Bloknaam |
|---|---|---|
| leidingelement zonder eigen symbool | cirkel | `VK_KLIC_HULPSTUK` |
| mof | cirkel met een streep dwars | elektra `VK_SKL-ET_HULP_MOF-SO`, datatransport `VK_SKL-DATA_HULP_MOF-SO`, anders `VK_KLIC_MOF` |
| afsluiter | twee driehoeken punt aan punt | riool `VK_SRI-HULP_AFSLUITER-SO`, andere leidingen `VK_SKL-WTB_HULP_AFSLUITER-SO`, elektra en datatransport `VK_KLIC_AFSLUITER` |
| verloopstuk (`verloop`, `verloopstuk`, `overgangsstuk`, `diameterovergang`) | trapezium | riool `VK_SRI-HULP_VERLOOPSTUK-SO`, andere leidingen `VK_SKL-WTB_HULP_VERLOOPSTUK-SO`, elektra en datatransport `VK_KLIC_VERLOOPSTUK` |
| materiaalovergang | rechthoek in twee helften | andere leidingen `VK_SKL-WTB_HULP_MATERIAAL-SO`, anders `VK_KLIC_MATERIAALOVERGANG` |
| aftakking (`tstuk`, `aftakzadel`, `aftakking`, `aftakmof`) | T | elektra `VK_SKL-ET_HULP_MOF_AFTAKMOF-SO`, anders `VK_KLIC_AFTAKKING` |
| eindkap (`eindkap`, `eindmof`, `eindsluiting`, `blindflens`) | streep dwars op het eind | elektra `VK_SKL-ET_HULP_MOF_EINDMOF-SO`, riool `VK_SRI-HULP_EINDKAP-SO`, andere leidingen `VK_SKL-WTB_HULP_EINDKAP-SO`, datatransport `VK_KLIC_EINDKAP` |
| aansluitpunt (`deliveryPoint`, `puntVanLevering`, `waterServicePoint`, `aansluitpunt`) | ruit | elektra `VK_SKL-ET_HULP_AANSLUITPUNT-SO`, andere leidingen `VK_SKL-WTB_HULP_AANSLUITPUNT-SO`, datatransport en riool `VK_KLIC_AANSLUITPUNT` |
| meetpunt kathodische bescherming (`kbMeetpunt`, `controleelement`) | driehoek | andere leidingen `VK_SKL-WTB_HULP_METER_KATHODISCHE BESCHERMING-SO`, anders `VK_KLIC_MEETPUNT` |
| aarding | steel met drie strepen | `VK_SKL-ET_AARDING-SO` |
| meter | cirkel met een M | andere leidingen `VK_SKL-WTB_HULP_METER_HOEVEELHEID-SO`, anders `VK_KLIC_METER` |
| overlengte (`overlengte`, `kabelrol`) | cirkel met een kleinere erin | elektra `VK_SKL-ET_KABELROL-SO`, datatransport `VK_SKL-DATA_KABELROL-SO`, anders `VK_KLIC_OVERLENGTE` |
| brandkraan (`fireHydrant`, `brandkraan`, of in het label) | cirkel met twee uitlopen | `VK_SKL-WATER_BRANDHYDRANT-SO` |
| lichtmast (`streetLight`, `lichtmast`, of in het label) | kleine cirkel met vier stralen | `VK_SIE-MEUBILAIR_PAAL_LICHTMAST-SO` |
| put (klasse Mangat; `inspectieput`, `handhole`, `put`) | twee cirkels | riool `VK_SRI-PUT_INSPECTIE-SO`, gas `VK_SKL-GAS_PUT-SO`, water `VK_SKL-WATERLEIDINGPUT-SO`, warmte `VK_SKL-WTB_WARMTENET_PUT-SO`, andere leidingen `VK_SKL-WTB_PUT-SO`, elektra en datatransport `VK_SIE-MEUBILAIR_PUT-SO` |
| kast (klasse Kast; `kast`) | rechthoek met een diagonaal | elektra `VK_SKL-ET_TERREINKAST-SO`, datatransport `VK_SKL-DATA_TERREINKAST-SO`, gas `VK_SKL-GAS_TERREINKAST-SO`, water `VK_SKL-WTB_HULP_TERREINKAST_WATER-SO`, riool `VK_SIE-MEUBILAIR_KAST_RIOOL-SO`, anders `VK_SIE-MEUBILAIR_KAST-SO` |
| mast of toren (klasse Mast of Toren; `mast`) | hoogspanning: vierkant met kruis; anders cirkel met kruis | hoogspanning en landelijk hoogspanningsnet `VK_SKL-ET_HS_MAST-SO`, laagspanning `VK_SKL-ET_LS_MAST-SO`, datatransport `VK_SKL-DATA_ZENDMAST-SO`, anders `VK_SIE-MEUBILAIR_MAST-SO` |
| technisch gebouw (klasse TechnischGebouw; `technischgebouw`, `substation`) | elektra: vierkant met bliksempijl; anders vierkant met een diagonaal | elektra `VK_SKL-ET_TRANSFORMATORSTATION-SO`, anders `VK_KLIC_TECHNISCH_GEBOUW` |

Tot en met 0.2.4 was elk leidingelement dezelfde cirkel (`VK_KLIC_ELEMENT`, 0,30 m) en hadden put, kast, mast en
gebouw elk één blok (`VK_KLIC_PUT`, `_KAST`, `_MAST`, `_GEBOUW`). Een tekening met die blokken houdt ze; zie de
wijzigingen van 0.2.5 voor de weg terug.

**Kleur en lijndikte.** De lagen hebben de kleur, het lijntype en de lijndikte van NLCS, met een paar
bewuste afwijkingen, zodat mantelbuizen, leidingen met gevaarlijke inhoud en zones met een eis opvallen en
bijzaken naar de achtergrond gaan:
- mantelbuizen, kabelgoten en kabelbedden: een band van 1,00 mm in de kleur van het thema (NLCS: 0,18); bij
  overig en weesleidingen grijs (8; NLCS: kleur 7) en bij riool vrij verval kleur 210 (hieronder). De
  omtrek van een mantelbuis staat op dezelfde laag maar is zelf 0,18 mm (een lijndikte op de omtrek): de band is
  dik, de rechthoek eromheen niet;
- buisleiding met gevaarlijke inhoud: kleur 20, doorgetrokken en 0,35 mm, ook de hulpstukken en
  mantelbuizen in kleur 20 (NLCS: kleur 40, net als petrochemie, lijntype `KL-BRANDSTOF-SO` en 0,18 mm);
- overige leidingen, een thema dat VLEA niet kent en de eigen topografie van de netbeheerders: grijs (8) en
  0,09 mm (NLCS: kleur 7 en 0,18 mm);
- weesleidingen: doorgetrokken (het NLCS-lijntype `KL-WEESLEIDING-SO` is een stip om de 8 m);
- riool vrij verval zonder stelsel, de rioolputten en de mantelbuis daarvan: kleur 210 (NLCS: rood, 10, de kleur
  van hoogspanning);
- de zone met een eis voorzorgsmaatregel: kleur 240 en 0,70 mm (NLCS: kleur 7 en 0,18 mm), en als de zone een vlak
  is ook een vulling (hieronder; NLCS kent geen doorzichtige laag).

**De vulling van een zone met een eis voorzorgsmaatregel.** Een zone die een vlak is, krijgt naast de rand een
vulling: een gevuld vlak in kleur 240, 80 % doorzichtig, op een eigen laag `B-OI-OG-ZONE_BELEMMERING_LEIDINGSTROOK-V`
(V is in NLCS een vlakvulling). Zo valt de zone op tussen de leidingen; door de vulling heen zie je de leidingen en
de ondergrond. De vulling ligt onder de lijnen (zoals elke arcering van VLEA) en boven een luchtfoto of kaartbeeld.
De rand (`…-G`) en de tekst met de eis (`…-T18`) blijven op hun eigen lagen. `VKINFO`, vervangen en wissen nemen de
vulling mee met de zone. Een zone die een lijn of een punt is, heeft geen vulling.
- Geen vulling: zet de laag `…-V` uit of bevries hem. Doorzichtiger of minder doorzichtig: verander de transparantie
  van die laag in het lagenbeheer. Dat werkt als de huidige transparantie van AutoCAD (`CETRANSPARENCY`) op DOORLAAG
  (ByLayer) staat, de standaard. Staat die op een getal, dan krijgt alles wat VLEA tekent die transparantie, ook de
  vulling (bijvoorbeeld 50 % in plaats van 80 %); zet `CETRANSPARENCY` dan vóór het laden op DOORLAAG.
- **Afdrukken:** de laag `…-V` drukt niet af (in het lagenbeheer staat Plot uit). Op papier en in een PDF staan de
  rand en de tekst met de eis, zoals in 0.2.3. Waarom: AutoCAD drukt transparantie alleen af als je in het
  afdrukvenster **Plot transparency** aanzet, en die staat standaard uit. Zonder die optie kwam de vulling dekkend op
  papier, en met een zwart-witte plotstijl (bijvoorbeeld `monochrome.ctb`) als een zwart vlak waarin de leidingen van
  de zone verdwijnen. Wil je de vulling toch op papier: zet in het lagenbeheer Plot aan voor de laag `…-V`, zet bij
  het afdrukken **Plot transparency** aan (of `PLOTTRANSPARENCYOVERRIDE` op 2) en druk af in kleur. `VKSTIJL` laat
  staan of een laag afdrukt.
- Exporteer je de zone naar Google Earth (`VKKMZ`), dan staat de vulling daar als vlak.
- Een levering die al in je tekening staat, krijgt de vulling pas als je hem opnieuw inleest.

Een rioolleiding met een stelsel houdt de NLCS-kleur van dat stelsel, en de mantelbuis van het persriool houdt
0,18 mm: die lagen gebruikt de rioleringskaart (`VKRIOOL`) ook, en één laag heeft in een tekening één stijl. Om
dezelfde reden is in de rioleringskaart een leiding of put zonder laag (`B-OI-RI-OVERIG_RIOOLLEIDING-G`,
`B-OI-RI-OVERIG_RIOOLPUT-S`, ook de meeste putten van een duikerstelsel) kleur 210; de andere lagen van de
rioleringskaart houden de NLCS-kleur. In het lagenbeheer staat bij een laag met een
afwijking ", VLEA-stijl" achter de beschrijving. Een lijndikte zie je op het scherm alleen als lijndikte
weergeven aan staat (`LWDISPLAY`); op een plot altijd. Staat een laag al in je tekening (ook van een levering
die je met een eerdere versie tekende), dan houdt die zijn stijl. Heeft VLEA zo'n KLIC-laag eerder gemaakt en
wijkt hij af, dan zegt een melding na het inlezen welke lagen het zijn; `VKSTIJL` met de keuze `Nlcs` zet ze
bij (zie 7). De laagnamen zijn NLCS, de afwijkende stijl is een keuze van VLEA: `VKSTIJL` `Nlcs` zet een KLIC-laag
op de stijl van VLEA, niet op die van de NLCS-objectentabel. Moet een tekening de stijl van de objectentabel
hebben, zet de lagen dan zo in je sjabloon vóór het inlezen: het gaat om de lagen met ", VLEA-stijl" in de
beschrijving, en de lijst hierboven noemt bij elke afwijking wat NLCS zegt.

**Dieptes** worden een label bij de plek, met de waarde zoals de netbeheerder hem levert:
"1,20 m-mv bk ±0,5 m" is 1,20 m onder maaiveld, bovenkant, nauwkeurigheid 0,5 m; "-0,85 m NAP bk ±0,3 m"
is een NAP-hoogte. "±onbekend" betekent dat de netbeheerder de nauwkeurigheid niet kent (of niet
levert): behandel die diepte als een indicatie, niet als een meting. Geeft de netbeheerder een eigen
label dat iets anders zegt dan de waarde, dan staan beide in het label ("0,00 m-mv bob ±onbekend (label
1.0)"); bij de waarde 0 met zo'n label volgt een waarschuwing: controleer die dieptes in de levering.
VLEA rekent nooit een hoogte van een kabel of leiding uit.

**Bijlagen** (de PDF's van de netbeheerders, zoals profielschetsen en de eisen voorzorgsmaatregel)
tekent VLEA niet. Open ze uit de levering; de opdrachtregel en de verantwoording noemen hoeveel er zijn,
en de plek van extra detailinformatie staat in de tekening (met `detailinfo=uit` niet, en dat staat
erbij).

**Opnieuw inlezen gaat per meldnummer.** VLEA onthoudt bij elk getekend object het meldnummer.
- Staat **dezelfde levering** (hetzelfde meldnummer) al in de tekening, dan vraagt VLEA
  **[Vervangen/Erbij/Overslaan]** en noemt het volgnummer en de datum van de levering in de tekening
  en van de nieuwe. **Vervangen** haalt de vorige versie van die levering weg, waar hij ook lag
  (handmatige wijzigingen daaraan verdwijnen). Enter = **Vervangen** als de nieuwe levering nieuwer of
  dezelfde is; is hij ouder, volgens zichzelf niet compleet, of niet te vergelijken (bijvoorbeeld omdat
  de verantwoording in de tekening is weggehaald), dan is Enter = **Overslaan** en zegt de vraag
  waarom. `vervangen=ja` in een script vervangt wel.
- Een **andere levering** (ander meldnummer) wist VLEA nooit, ook niet met `vervangen=ja` in een
  script. Overlapt de nieuwe levering een andere, dan komt hij erbij en meldt VLEA "overlapt met een
  andere levering (…)": in de overlap kunnen kabels en leidingen dubbel staan.
- Een levering zonder meldnummer (of een KLIC-import uit een testversie van vóór 0.2) telt als een
  andere levering: die wordt nooit door een nieuwe import gewist.

`VKWISSEN` toont een KLIC-import als "KLIC-levering" en wist KLIC als geheel (sleutel `klic`), ook de
bronvermeldingen in de tekeningeigenschappen; `VKINFO` toont bij een KLIC-object de gegevens uit de levering,
met het meldnummer ("Levering: …") en de status en ligging in het Nederlands. Daarnaast draagt elk KLIC-object de
gegevens uit de levering in het formaat van het VLEA-portaal (XData `VLEA_KLIC`), voor ander VLEA-gereedschap dat
KLIC-gegevens leest. Dat vindt een KLIC die deze plugin in de tekening zet, nu nog niet: het zoekt de KLIC in een
xref of op een laag met "KLIC" in de naam, en de KLIC-lagen van deze plugin hebben dat niet. Je ziet er in de
tekening niets van, en `VKINFO` toont ze niet apart. Een levering die je met een versie van vóór
0.2.4 tekende, krijgt ze pas als je hem opnieuw inleest.

In een script, één regel per vraag, met `FILEDIA` op 0. Staat er een spatie in het pad, zet het pad
dan tussen aanhalingstekens:

```text
FILEDIA
0
VKKLIC
C:\Leveringen\Levering_26X0000001.zip
vervangen=ja
FILEDIA
1
```

## 7. Lagen en stijl
- VLEA tekent op NLCS-lagen. Bestaat een laag al in je tekening, dan blijft jouw instelling staan. Dat
  geldt ook voor een laag die een eerdere versie van VLEA maakte: krijgt een laag in een nieuwe versie een
  andere kleur of lijndikte, dan zie je dat alleen op een nieuwe laag. Bij een KLIC-levering zegt een melding na
  het inlezen welke KLIC-lagen die VLEA eerder maakte een andere kleur, lijndikte, lijntype of transparantie hebben. Wil je de
  nieuwe stijl in een bestaande tekening: bij KLIC `VKSTIJL` met de keuze `Nlcs` (hieronder); of wis de kaart of
  levering (`VKWISSEN`), verwijder de lege lagen (bijvoorbeeld met `PURGE`) en laad opnieuw. Wil je juist je eigen
  stijl, zet de lagen dan zo in je sjabloon: lagen die je zelf maakte, past VLEA nooit aan, ook niet met `VKSTIJL`.
- `VKSTIJL`: NLCS-kleuren of grijze onderlegger (kleur 252), en terugzetten naar de kleur van
  daarvoor. Met `Nlcs` krijgt een KLIC-laag ook de lijndikte, het lijntype en de transparantie van VLEA (alleen de
  vullaag van een zone is doorzichtig, 80 %; de andere zijn dekkend). Of een laag afdrukt (Plot in het lagenbeheer),
  verandert `VKSTIJL` niet; op de andere lagen zet
  `VKSTIJL` alleen de kleur. `VKSTIJL` werkt op alle lagen die VLEA maakte, tegelijk: kies je `Nlcs` om een
  KLIC-levering bij te werken, dan krijgt ook een kaart die je grijs had gemaakt haar kleur terug (daarna kan
  `VKSTIJL` `Grijs` weer, maar dat maakt ook de KLIC grijs). Voor de knoppen van palet en lint kies je de stijl
  vóór het laden in de instellingen (tandwiel, **Stijl**).
- Alle teksten die VLEA tekent (ook de attributen in blokken en de bronvermelding) staan in de tekststijl `VLEA_ISO`
  met het lettertype `isocp.shx`, een lijnlettertype dat bij AutoCAD hoort: een tekst wordt geplot met de lijndikte
  van zijn laag. Bestaat `VLEA_ISO` al in je tekening, dan blijft jouw instelling staan. Een paar tekens kent dat
  lettertype niet; die worden in de tekening een gewoon teken: het weglatingsteken (…) wordt drie punten, een
  gedachtestreepje (– of —) of een minteken (−) een streepje, een gekruld of laag aanhalingsteken („) een recht, ≤ en ≥
  worden `<=` en `>=`, en het diameterteken (⌀) wordt Ø. Andere tekens die `isocp.shx` niet kent (bijvoorbeeld de
  meeste Griekse letters of ‰) worden een vraagteken. Staan die in je teksten, zet dan met `STYLE` het lettertype van
  `VLEA_ISO` op `isocpeur.ttf` (tot en met 0.2.3 het lettertype van VLEA; het geldt dan voor alle teksten in die stijl).
- Het NAP-gereedschap in een lengteprofiel tekent op twee eigen lagen buiten NLCS: `HDD-NAP-REFERENTIE` (kleur 7) en
  `HDD-NAP-LEADER` (kleur 1), dezelfde als het LISP-script NAPLEADER. `VKSTIJL` met `Grijs` laat die twee staan: een
  NAP-leider hoort bij het profiel, niet bij de onderlegger. `Nlcs` en `Terug` gelden er wel voor.
- De maatlijnen van `VKMAAT` staan op `X-XX-AL-REFERENTIE-M` (kleur 7, 0,18 mm). Ook die laag laat `VKSTIJL` met
  `Grijs` staan: een maat is je eigen werk, geen onderlegger.
- Stuur je een tekening naar iemand zonder VLEA: gebruik eTransmit, zodat `NLCS.shx` meegaat.

## 8. Bronvermelding
De bronvermelding staat in de tekeningeigenschappen (een KLIC-levering heeft per levering een eigen
eigenschap: "Bronvermelding klic <meldnummer>") en kan als tekst in de tekening komen (optie
"bronvermelding plaatsen"). Verplaats die tekst naar je layout, zodat hij op de plot staat. Bij
CC BY-bronnen (BGT, ook als kaartbeeld, BRT, kadaster, luchtfoto) is naamsvermelding verplicht wanneer je de tekening deelt
of publiceert. De zones langs waterkeringen (`VKZONERINGEN`) vallen onder CC BY-SA 4.0 ("gelijk delen"):
die van de waterschappen zijn CC BY-SA 4.0, de legger van Rijkswaterstaat is CC0 1.0, en VLEA houdt voor
de hele kaart de strengste licentie van de twee aan. Deel je die zones (of een bewerking ervan) verder,
dan onder dezelfde of een compatibele licentie. De licentie spreekt van delen met het publiek; of een
tekening aan één opdrachtgever daaronder valt, beoordeelt VLEA niet. Wat dat betekent, staat in de
README. Wil je dat niet, wis de zones dan in de kopie die je verstuurt (`VKWISSEN`, kaart `zoneringen`).

## 9. Over VLEA
`VKOVER` toont de versie, de licenties (de licentie van de plugin, CC BY 4.0 voor NLCS), de regels
voor naam en logo, de privacy, de bronnen en alle commando's met per kaart de grens. **Over VLEA** onderaan het
palet toont hetzelfde met het logo, zonder de commando's en de grenzen.

### Hulp en website (`VKHELP`, `VKWEBSITE`)
`VKHELP` toont op de opdrachtregel de versie, de map waarin VLEA geïnstalleerd is, waar je instellingen
en het logboek staan, en hoe je bijwerkt (`VKUPDATE`), en opent deze handleiding in je browser.
`VKWEBSITE` opent de website van VLEA (`https://vanleeuwenea.nl`). Beide openen alleen je eigen browser;
de plugin maakt daarbij zelf geen verbinding. In de AutoCAD-kern zonder schermen (scripts via
`accoreconsole`) gaat er geen browser open: dan staat alleen het adres op de opdrachtregel. Een script in
AutoCAD met schermen opent de browser wel.

In het palet openen de link **vanleeuwenea.nl** en **?** de website en deze handleiding rechtstreeks in
je browser, zonder commando: een commando waar je mee bezig bent, loopt door. Lukt het openen niet, dan
staat het adres op de opdrachtregel. De lintknop **Help** doet hetzelfde als `VKHELP`.

### Netwerk
De kaarten komen van PDOK. Twee uitzonderingen: de zones langs waterkeringen van Rijkswaterstaat
komen uit de legger van Rijkswaterstaat (`geo.rijkswaterstaat.nl`; zet de optie `rws` uit als je dat
niet wilt), en voor de sonderingen en boringen praat VLEA met de openbare uitgifte van de BRO
(`publiek.broservices.nl`): het zoekt daar sonderingen of boringen in je gebied en haalt ze op, verder niets. Voor
de peilbuizen zoekt VLEA bij PDOK (de kengegevens van de BRO) en haalt het bij de BRO alleen de meetreeksen van de
gekozen peilbuizen op (met de optie `standen` uit: niets bij de BRO).

VLEA kijkt hoogstens één keer per dag bij GitHub (`api.github.com`) of er een nieuwere versie is en
zet dan een regel onderaan het palet. GitHub ziet daarbij je IP-adres en het versienummer; verder
gaat er niets mee, en er wordt niets automatisch bijgewerkt. Uitzetten kan in de instellingen
(tandwiel, **Algemeen**), met het vinkje "Eén keer per dag kijken of er een nieuwe versie is".

Bij het openen van het palet kijkt VLEA hoe de bronnen ervoor staan (zie 2, Status van de bronnen): hoogstens één
keer per tien minuten vanzelf, per kaart een of twee kleine verzoeken aan dezelfde bron (PDOK, de BRO en, met de
optie `rws` aan, de legger van Rijkswaterstaat), altijd in een vast testgebied en nooit in jouw gebied. Dat zijn de
enige verzoeken aan die bronnen waar je zelf niets voor doet. De bron ziet daarbij je IP-adres en het versienummer.
Uitzetten kan in de instellingen (tandwiel, **Algemeen**), met het vinkje "Status van de bronnen tonen".
`VKSTATUS` vraagt altijd alle bronnen, ook de legger van Rijkswaterstaat, ook als de optie `rws` of "Status van de
bronnen tonen" uit staat: het is een commando dat je zelf start.

Een KLIC-levering (`VKKLIC`) en eigen grondonderzoek (`VKGEF`) leest VLEA alleen van je eigen schijf; daarbij
maakt VLEA geen verbinding.

Alleen als je `VKUPDATE` start (typen, de knop **Bijwerken** in het palet of op het lint, of de regel
"Nieuwe versie beschikbaar" onderaan het palet), maakt VLEA ook verbinding met `github.com` en
`release-assets.githubusercontent.com` (de download, zie hieronder). `VKHELP`, `VKWEBSITE`, **Help** op
het lint en in het palet de knop **?** en de link **vanleeuwenea.nl** openen alleen je browser, net als
`VKGOOGLE`, `VKSTREETVIEW`, `VKSTREETSMART` en `VKDINO` (zie 11). Een
doorverwijzing naar een adres buiten deze lijst volgt VLEA niet, en cookies bewaart en stuurt het niet.

Na `VKKMZ` opent Google Earth het bestand (alleen in AutoCAD met schermen). Google Earth haalt dan zelf
kaartbeelden bij Google op voor dat gebied; dat doet Google Earth, niet de plugin.

### Een nieuwe versie ophalen (`VKUPDATE`)
Typ `VKUPDATE`. VLEA vraagt bij GitHub wat de nieuwste versie is. Is die nieuwer dan de jouwe, dan:

1. downloadt VLEA `VLEA-AutoCAD.zip` en `SHA256SUMS.txt` van die versie (van `github.com`, dat de
   bestanden via `release-assets.githubusercontent.com` levert);
2. controleert VLEA de SHA-256 van de zip. Klopt die niet, dan gaat alles weg en zegt VLEA dat;
3. pakt VLEA de zip uit in `%LOCALAPPDATA%\VLEA-AutoCAD\updates\<versie>\` en opent die map in
   Verkenner.

Daarna: **sluit AutoCAD en dubbelklik `Installeer.bat` in die map.** VLEA installeert nooit zelf en
start geen scripts. Je kunt ook het installatieprogramma (`VLEA-AutoCAD-Setup.exe`) van de nieuwe versie
downloaden en openen: het vervangt de versie die er staat.
Is er nog geen versie uitgebracht of heb je de nieuwste al, dan zegt `VKUPDATE` dat
en downloadt niets. Esc of **Annuleren** stopt het ophalen; er blijft dan niets staan. `VKUPDATE` stelt
geen vragen en werkt dus ook in een script. In AutoCAD met schermen opent de map in Verkenner, ook
vanuit een script; in de AutoCAD-kern zonder schermen (`accoreconsole`) niet (de melding noemt hem wel).

## 10. Google Earth
### Naar Google Earth (`VKKMZ`)
- Kies objecten, of kies ze eerst en start dan `VKKMZ`. **Enter** zonder iets te kiezen = alle
  objecten van VLEA-kaarten in het gebied van de tekening (heeft de tekening nog geen gebied: alle
  VLEA-kaarten), zonder de objecten van een KLIC-levering (zie **KLIC** hieronder).
- Kies je **één open lijn of polylijn**, dan wordt dat een **boortracé**: de lijn, de plekken "Begin"
  en "Eind", en de lengte (horizontaal, in de tekening gemeten) in de omschrijving.
- Verder: lijnen, polylijnen en bogen als lijn (bogen benaderd tot op 5 cm), gesloten polylijnen,
  cirkels en arceringen als vlak (een gat blijft een gat), punten en blokken als plek (naam = de eerste
  ingevulde attribuutwaarde, bij een ingelezen KML-punt zijn eigen naam, anders de bloknaam), teksten
  als label. Per laag een map, in de kleur van
  de laag. Maatvoering, rasterafbeeldingen, 3D-objecten en het hoogtemodel gaan niet mee; de
  opdrachtregel noemt ze.
- Het bestand komt naast de tekening in de map `<tekening>_kaarten`: `<tekening>_googleearth.kmz`,
  of `<tekening>_boortrace.kmz`. Is de tekening nog niet opgeslagen, dan in
  `%LOCALAPPDATA%\VLEA-AutoCAD\export`. Een bestand met dezelfde naam wordt vervangen; staat het nog
  open (bijvoorbeeld in Google Earth), dan krijgt het nieuwe bestand een tijdstempel in de naam.
- Daarna opent VLEA het bestand met het programma dat bij .kmz hoort (Google Earth Pro, als dat
  geïnstalleerd is). Is er geen programma voor .kmz, dan zegt VLEA dat, met het pad.
- Standaard komt er ook een los .kml-bestand naast de .kmz (voor programma's die geen .kmz lezen);
  `kml=uit` schrijft alleen de .kmz. Staat er dan nog een ouder los .kml met dezelfde naam (van een
  eerdere export), dan laat VLEA dat staan (misschien heb je het zelf bewerkt) en zegt de opdrachtregel
  dat het niet bij de nieuwe .kmz hoort. Op de opdrachtregel vraagt `VKKMZ` de opties na het kiezen;
  Enter = standaard.
- De omschrijving van het bestand noemt de bronvermelding van de VLEA-kaarten erin: deel je het
  bestand, dan geldt de naamsvermelding van CC BY ook daar.
- **KLIC:** KLIC-gegevens zijn vertrouwelijk: volgens de WIBON (art. 4 lid 2) mag je ze alleen aan
  anderen geven voor zover dat noodzakelijk is om graafschade te voorkomen, of voor de oriëntatie op een
  verzoek tot medegebruik of coördinatie. Daarom
  neemt **Enter** de objecten van een KLIC-levering niet mee; de opdrachtregel zegt hoeveel dat er zijn
  ("… objecten uit een KLIC-levering niet meegenomen; selecteer ze zelf als je ze wilt delen"). Wil je
  ze toch in het bestand, kies ze dan zelf. Dan noemt de omschrijving ook de herkomst (Kadaster en
  netbeheerders), de zin "Informatief; de levering zelf blijft leidend bij graafwerk." en de
  vertrouwelijkheid, en zegt de opdrachtregel dat ook. Het meldnummer staat nergens in het bestand, ook
  niet per object: waar het in een naam of omschrijving zou staan (de id's van het aanvraaggebied, de
  teksten van de bronvermelding en de verantwoording), staat "[meldnummer weggelaten]". De bestandsnaam
  volgt de naam van je tekening; staat het meldnummer daarin, hernoem dan het bestand voordat je het deelt.
- VLEA rekent RD om naar lengte- en breedtegraad met de openbare benaderingsformules: ruim binnen 1 m,
  genoeg voor Google Earth, niet voor landmeten. Objecten die niet in RD liggen (lokale coördinaten),
  gaan niet mee.

### Uit Google Earth (`VKKMLIMPORT`)
- Kies een .kml- of .kmz-bestand, bijvoorbeeld opgeslagen uit Google Earth. Met `FILEDIA` op 0 typ
  je het pad op de opdrachtregel, of `~` voor het venster.
- Lijnen worden polylijnen, vlakken gesloten polylijnen (elk gat een eigen gesloten polylijn), punten
  het symbool `VK_PUNT` met de naam als label. Alles op vaste lagen: `X-XX-AL-REFERENTIE-G` (lijnen en
  vlakken), `X-XX-AL-REFERENTIE-S` (punten) en `X-XX-AL-REFERENTIE-T18` (labels).
- Naam, omschrijving en de extra gegevens uit het bestand staan bij elk object: `VKINFO`. Wissen met
  `VKWISSEN` en kaart `kml` (alle ingelezen KML-bestanden), of met Ctrl+Z direct na het inlezen.
- Hoogtes worden niet overgenomen: alles staat op hoogte 0 (de hoogte van een punt staat bij
  `VKINFO`). Gegevens buiten Nederland worden niet ingelezen. VLEA meldt beide.
- Hetzelfde bestand nog eens inlezen zet alles er nog een keer bij (er is geen vraag
  Vervangen/Erbij/Overslaan).
- VLEA volgt geen koppelingen naar internet in een KML (NetworkLink) en leest geen afbeeldingen,
  3D-modellen of tijdsporen; de opdrachtregel noemt wat is overgeslagen.

### In een script
Eén regel per vraag; een lege regel is Enter. Alle VLEA-kaarten in het gebied (zonder KLIC), alleen de
.kmz (zonder losse .kml):

```text
VKKMZ

kml=uit
```

De laatst getekende polylijn als boortracé (`_L` kiest het laatste object, de lege regel sluit het
kiezen af, de tweede lege regel neemt de standaardopties):

```text
VKKMZ
_L


```

Een KML inlezen zonder venster:

```text
FILEDIA
0
VKKMLIMPORT
D:\projecten\voorbeeld.kml
FILEDIA
1
```

In de AutoCAD-kern zonder schermen opent `VKKMZ` niets; het meldt alleen waar het bestand staat. Een
script in AutoCAD met schermen opent het bestand wel.

## 11. De plek bekijken in je browser
Met één commando of knop open je de plek uit je tekening in je browser. Typ het commando, of klik in het
palet onder **Bekijk de plek** (op het lint: paneel **Bekijk de plek**) op de knop van de dienst.

| Commando | Knop | Wat opent er |
|---|---|---|
| `VKGOOGLE` | Google Maps | Google Maps met een speld op de plek. |
| `VKSTREETVIEW` | Street View | Street View van Google: het dichtstbijzijnde panorama. Wijs je een tweede punt aan, dan kijk je die kant op. |
| `VKSTREETSMART` | StreetSmart | StreetSmart van Cyclomedia, op de RD-coördinaten. Daarvoor heb je een eigen account van Cyclomedia nodig (vaak via een gemeente, waterschap of netbeheerder); zonder account zie je alleen het inlogscherm. |
| `VKDINO` | DINOloket | De kaart van DINOloket (van TNO), ingezoomd op de plek; de plek ligt in het midden van de kaart, zonder speld. Zet bovenaan in DINOloket **Bodem- en grondonderzoek** aan om de sonderingen en boringen te zien. Staat de kaart toch ergens anders, zoek dan in het zoekveld op de coördinaten van de opdrachtregel (hele meters, bijvoorbeeld `155000,463000`). |

- Wijs een punt aan of typ `x,y` (RD, meters); **Enter = midden van het beeld**.
- Bij `VKSTREETVIEW` volgt "Kijkrichting: wijs een tweede punt aan (Enter = zonder kijkrichting)". VLEA
  rekent de richting uit in lengte- en breedtegraad, niet langs het RD-raster (dat wijkt tot ruim een
  graad af van het echte noorden).
- De opdrachtregel noemt de plek in RD en in WGS84 (breedte- en lengtegraad) en het adres dat opent. Het
  adres bestaat alleen uit die coördinaten; niets anders uit je tekening gaat mee.
- In de papierruimte van een layout weigert VLEA: daar is een punt een plek op het blad, geen
  RD-coördinaat. Ga naar de modelruimte of dubbelklik in een viewport. Een plek buiten het RD-stelsel
  (lokale coördinaten) weigert VLEA ook, en de tekening moet in meters staan (zie 1).
- **Street View** toont het panorama dat het dichtst bij de plek is opgenomen. Bij een tracé door het
  weiland kan dat een eind verderop liggen: kijk na of het de plek is.
- **StreetSmart:** of je na het inloggen meteen op de plek uitkomt, hangt af van Cyclomedia; dat is nog
  niet met een account getest. Kom je er niet, zoek dan in StreetSmart op de RD-coördinaten van de
  opdrachtregel.
- **DINOloket:** de kaart opent op de plek, met de schaalbalk op 20 m (de viewer rondt de schaal af op
  ongeveer 1:977; een browservenster van 1600 pixels breed toont ongeveer 390 meter, een breder venster
  meer). TNO beschrijft dit adres niet; zou een nieuwe versie van DINOloket er anders mee omgaan, dan opent
  de kaart zonder plek en zoek je in DINOloket op de coördinaten van de opdrachtregel.
- **Privacy:** Google, Cyclomedia en TNO (DINOloket) krijgen de coördinaten van het gekozen punt: die dienst
  ziet die plek (en wat de pagina van die dienst zelf laadt, zoals analysediensten), dus waar je project
  ligt (bij Google ook je Google-account als je in je browser bent ingelogd). Bij DINOloket staat de plek
  achter het #-teken van het adres: je browser stuurt dat deel niet mee met het eerste verzoek, maar de
  pagina leest het en haalt dan de kaart voor die plek op bij TNO en de achtergrondkaart bij PDOK; TNO en
  PDOK zien dus die plek. De plugin maakt zelf geen verbinding: je browser opent het adres.
- In de AutoCAD-kern zonder schermen (`accoreconsole`) gaat er geen browser open: dan staat alleen het
  adres op de opdrachtregel. Een script in AutoCAD met schermen opent de browser wel.

### In een script
Eén regel per vraag; een lege regel is Enter. De plek in Google Maps, dezelfde plek in Street View met de
kijkrichting naar het oosten, en DINOloket voor het midden van het beeld:

```text
VKGOOGLE
155000,463000
VKSTREETVIEW
155000,463000
155100,463000
VKDINO

```

### Geografische plek in AutoCAD (`VKGEOPLEK`)
Met `VKGEOPLEK` (in het palet bij het gereedschap: **Geografische plek**) zet je de geografische plek van de
tekening op RD (EPSG:28992; in AutoCAD heet dat coördinatensysteem `Amersfoort-RDNew`). Dan weet AutoCAD
waar de tekening ligt: met `GEOMAP` zet je de online kaart van AutoCAD onder je tekening (daarvoor ben je
aangemeld bij Autodesk), en `GEOMARKER` toont de markering van de plek. Er opent geen browser.

- VLEA zet de plek zo dat de tekeningcoördinaten precies de RD-coördinaten zijn, in meters en met het
  noorden langs de y-as: er verschuift, draait of schaalt niets. Dat klopt als je tekening in RD staat,
  zoals alles wat VLEA tekent.
- De markering komt in het midden van het gebied dat je koos (zie 3), en zonder gebied in het midden van
  het beeld. Waar de markering staat, verandert niets aan de plek van je tekening.
- Heeft de tekening al een andere geografische plek (een ander coördinatensysteem, of RD met een
  verschoven of gedraaide tekening), dan noemt de opdrachtregel die plek en vraagt
  [Vervangen/Overslaan]; Enter = Overslaan. Heeft de tekening deze plek al, dan verandert er niets en zegt
  de opdrachtregel dat.
- Staat de tekening al op RD onder een andere code van AutoCAD, bijvoorbeeld de oudere
  `Netherlands-RDNew`, dan zegt de opdrachtregel dat het ook RD is, maar een andere definitie. Die rekent
  anders om naar lengte- en breedtegraad, dus de online kaart kan iets anders vallen. Met Vervangen krijg je
  `Amersfoort-RDNew`; met Overslaan blijft de tekening zoals ze was.
- VLEA zet niets in een tekening die niet in meters staat (zie 1), in de papierruimte als de tekening nog
  geen gebied heeft (ga naar de modelruimte of kies eerst een gebied), als het midden van het beeld buiten
  het RD-stelsel ligt (lokale coördinaten), en als AutoCAD het coördinatensysteem `Amersfoort-RDNew` niet
  kent.
- De plek weer weghalen: `GEOREMOVE` van AutoCAD.
- Civil 3D en Map 3D hebben ook een eigen instelling voor het coördinatensysteem van de tekening; kijk daar
  na of die RD is.
- VLEA maakt hierbij geen verbinding. De online kaart is van AutoCAD zelf: AutoCAD haalt de kaartbeelden
  op bij Autodesk, en die ziet dan welk gebied je bekijkt.
- In een script: `VKGEOPLEK` vraagt alleen iets als de tekening al een andere plek heeft; zet er dan een
  regel `Vervangen` of `Overslaan` achter.

## 12. Problemen oplossen
| Wat je ziet | Wat je doet |
|---|---|
| Je browser of Windows waarschuwt bij `VLEA-AutoCAD-Setup.exe` ("wordt niet vaak gedownload", of een blauw venster van Windows) | Het programma is niet ondertekend. Vertrouw je de download (zie "Download controleren" in de README), kies dan in je browser dat je het bestand wilt behouden en in Windows **Meer informatie** en daarna **Toch uitvoeren**. |
| Windows zegt dat Smart App Control het installatieprogramma (of `Installeer.bat`) heeft geblokkeerd | Smart App Control van Windows 11 laat niet-ondertekende programma's en scripts van internet niet toe, en heeft geen knop om door te gaan. VLEA is niet ondertekend; op die pc lukt installeren zo niet. Meld het via de issues, dan weten we voor hoeveel gebruikers dit speelt. |
| Het installatieprogramma zegt "AutoCAD draait nog" | Sluit alle AutoCAD-vensters en klik op **Opnieuw proberen**. Er is niets gewijzigd. |
| Het installatieprogramma zegt "Het is niet gelukt" | De zin eronder zegt wat er wel en niet gewijzigd is; vaak helpt even wachten en **Opnieuw proberen** (een virusscanner kan nieuwe bestanden kort vasthouden). De technische melding staat in `%LOCALAPPDATA%\VLEA-AutoCAD\logs\setup.log`, zonder je Windows-naam; zet dat bestand bij je melding. |
| AutoCAD vraagt of de plugin geladen mag worden (venster "Security - Unsigned Executable File", want de DLL's zijn niet ondertekend, of "File Loading - Security Concern") | Kies **Load** of **Load Once** (AutoCAD heeft geen Nederlandse knoppen). Installeer opnieuw (met het installatieprogramma of `Installeer.bat`) als AutoCAD het elke keer vraagt. |
| Geen lint-tabblad VLEA en geen `VKPALET` | Controleer met `APPAUTOLOAD` dat de waarde 14 is; start AutoCAD opnieuw. |
| "De tekeningeenheid is millimeters" (of een andere eenheid), of alle kaarten in het palet grijs | Typ `UNITS` en kies bij **Insertion scale** (invoegschaal) "Meters" (of typ `INSUNITS` en dan `6`). Een nieuwe tekening uit het metrische standaardsjabloon staat in millimeters. Teken je zelf al in millimeters, begin dan met een tekening in meters. |
| Een kaart staat grijs | De reden staat eronder (of, bij de eenheid, boven de kaarten). Het gebied is te groot voor die kaart, (AHN) je werkt niet in Civil 3D, in de instellingen staan alle onderdelen van die kaart uit, of de tekening staat niet in meters. Bij een lange, schuine strook telt voor AHN en de sonderingen de rechthoek om de strook (zie 4). |
| `VKHELP`, `VKWEBSITE`, de link of **?** in het palet, of een knop onder **Bekijk de plek** opent geen browser | In de AutoCAD-kern zonder schermen (scripts via `accoreconsole`) gaat er bewust geen browser open; een script in AutoCAD met schermen opent hem wel. Anders (bijvoorbeeld een beleid dat de browser blokkeert): open het adres op de opdrachtregel zelf ("De browser kon niet worden geopend. Open het adres zelf: …"). |
| "Je werkt in de papierruimte" bij `VKGOOGLE`, `VKSTREETVIEW`, `VKSTREETSMART` of `VKDINO` | Ga naar de modelruimte (of dubbelklik in een viewport) en start het commando opnieuw. |
| StreetSmart toont alleen het inlogscherm | Je hebt een account van Cyclomedia nodig. Kom je na het inloggen niet op de plek, zoek dan op de RD-coördinaten van de opdrachtregel. |
| In het palet staat "wacht – zie opdrachtregel" | VLEA vraagt iets op de opdrachtregel, bijvoorbeeld [Vervangen/Erbij/Overslaan] omdat die kaart al in dit gebied staat. Beantwoord de vraag daar. |
| In een script of in AutoLISP: "Het commando is gestopt en dit antwoord heeft niets gewijzigd; wat daarna komt, wordt weer als commando gelezen." | Een antwoord in je script past niet bij de vraag: een tikfout, een deel van een sleutel (`bgtb`), een sleutel die niet in de tekening staat, of een lege regel waar geen standaard is. De regel ervoor zegt welk antwoord het was en welke keuzes er zijn. Verbeter het antwoord in het script; zie 4 ("Een antwoord dat niet past"). Er is niets gewist of geladen. |
| "overlapt met een andere levering" (bij meer dan één: "overlapt met 2 andere leveringen") bij `VKKLIC` | De nieuwe levering is erbij gezet; de andere levering of leveringen staan er nog. Wil je alleen de nieuwe, wis dan eerst met `VKWISSEN` (sleutel `klic`; dat wist alle KLIC-imports) en lees de nieuwe opnieuw in. |
| Er staan minder sonderingen dan er in het gebied liggen | Zonder keuze tekent VLEA de 25 dichtst bij het midden van het gebied (bij een strook van `VKCONTOUR`: bij de lijn); de melding zegt hoeveel er niet getekend zijn. Kies een hoger aantal in de instellingen (tandwiel, Kaarten, Sonderingen (BRO)), of typ bij het commando `aantal=50`, `aantal=100` of `aantal=alle`, en laad opnieuw. |
| Eén sondering te veel, of een gat in de rij sondeerplots | Weghalen: `VKWISSEN`, keuze `Selectie`, de sondering aanklikken en Enter (symbool, label en plot gaan samen weg). De andere plots schuiven dan niet op; laad opnieuw met Vervangen voor een nette rij (zie 4, Sonderingen weghalen). |
| "Sla de tekening eerst op" bij de luchtfoto, de BRT (het plaatje) of het kaartbeeld van de BGT | Het beeld komt in een map naast de tekening; die bestaat pas na opslaan. Klik **Opslaan** onder de kaart in het palet. |
| In het palet External References (`XREF`) staan beelden van VLEA (`luchtfoto_…`, `brt_…`, `bgtbeeld_…`) zonder beeld in de tekening, als **Unreferenced** | Die bleven achter na wissen of Vervangen met 0.2.3 of eerder; sinds 0.2.4 haalt VLEA ze zelf weg. Klik er met de rechtermuisknop op en kies **Detach**. Het bestand in `<tekening>_kaarten` blijft staan. |
| `VKBGT` (of een ander kaartcommando) is onbekend | De plugin is niet geladen. Controleer met `APPAUTOLOAD` dat de waarde 14 is en start AutoCAD opnieuw. |
| Laden duurt lang of faalt | Controleer je internetverbinding naar PDOK; probeer een kleiner gebied. |
| `VKUPDATE`: "GitHub weigert het verzoek (HTTP 403)" | Zonder account staat GitHub 60 verzoeken per uur per netwerk toe. Probeer het over een uur opnieuw, of download de zip zelf via de releasepagina. |
| `VKUPDATE`: "De download zou via … lopen" | GitHub stuurt de download naar een adres dat VLEA niet vertrouwt; er is niets gedownload. Download de zip zelf via de releasepagina en meld het als issue. |
| "… objecten uit een KLIC-levering niet meegenomen" bij `VKKMZ` | Enter neemt geen KLIC mee: KLIC-gegevens zijn vertrouwelijk (WIBON). Wil je ze toch delen, kies de objecten dan zelf (zie 10). |
| Na `VKKMZ` opent Google Earth niet | Er is geen programma gekoppeld aan .kmz-bestanden. Installeer Google Earth Pro, of open het bestand zelf: het pad staat op de opdrachtregel. |
| `VKKMLIMPORT` meldt "buiten Nederland" | De gegevens liggen niet in Nederland, of in het bestand zijn lengte en breedte verwisseld. |
| "Dit is een oud Excel-bestand (.xls)" of "met een wachtwoord beveiligd" bij `VKPUNTEN` | Open het bestand in Excel en sla het op als `.xlsx` of als `.csv` (zonder wachtwoord), en kies dat bestand. |
| `VKPUNTEN` zet de punten op een rare plek, of zegt dat X en Y verwisseld lijken | Kies `Kolommen` en wijs X (oost, in Nederland tussen 0 en 280.000) en Y (noord, tussen 300.000 en 620.000) zelf aan. Kijk naar het eerste punt dat VLEA laat zien. Staan de punten in graden of in een eigen stelsel, reken ze dan eerst om naar RD. |
| `VKPUNTEN` vindt geen kolommen, of vraagt naar het decimaalteken | Sla het bestand in Excel op als `.xlsx` of als CSV. Staan er decimale komma's én punten in, kies dan het teken van de coördinaten. |
| Een punt van `VKPUNTEN` is niet te zien | Hoe een punt eruitziet, bepalen `PDMODE` en `PDSIZE` van de tekening; zet bijvoorbeeld `PDMODE` op 3. De leider wijst het punt aan. |
| Leiders van `VKPUNTEN` overlappen | De samenvatting zegt hoeveel leiders niet vrij staan. Verschuif ze met de grip, kies bij `Schaal` de schaal waarop je afdrukt, of kies `Tekst` en dan `Naam` voor kortere teksten. |
| Een NAP-leider toont een hoogte die niet klopt | Heb je hem verschoven, klik dan **NAP herberekenen** (`VKNAPUPDATE`). Klopt het daarna nog niet: kijk of het UCS op Wereld staat (`UCS`, Enter) en of de referentie en de verticale schaal goed zijn; stel ze zo nodig opnieuw in met **NAP-referentie** en kies `Ja`. |
| `VKNAPLEADER` zegt dat de referentie in de andere ruimte staat | De referentie hoort bij de modelruimte of bij één layout. Ga naar die ruimte, of stel in de ruimte waar je werkt een nieuwe referentie in (`VKNAPSET`); de vorige wordt dan vervangen. |
| "Dit bestand is geen KLIC-levering" | Kies de zip van het Kadaster of de XML `GI_gebiedsinformatielevering_….xml`, niet een bijlage of een bestand van een KLIC-viewer. |
| "Kies de XML van de levering … of de zip" direct na het pad | Je koos een ander bestand of een map. Met `FILEDIA` = 0 zet AutoCAD `.xml` achter een getypt pad met een andere extensie. Typ het volledige pad naar de zip of de XML. |
| De vraag bij dezelfde KLIC-levering heeft Overslaan als standaard | De nieuwe levering is ouder, niet compleet of niet te vergelijken met die in de tekening; de vraag zegt welke. Typ `V` als je toch wilt vervangen. |
| `VKKLIC`, `VKGEF` of `VKKMLIMPORT` vraagt het pad op de opdrachtregel in plaats van een venster | `FILEDIA` staat op 0 (bijvoorbeeld na een afgebroken script). Typ `~` voor het venster (bij `VKGEF` dan het venster van AutoCAD, voor één bestand), of zet `FILEDIA` op 1. |
| AutoCAD reageert even niet na een grote KLIC-levering | Het tekenen van 100.000 objecten of meer duurt 10 tot 20 seconden en is niet af te lezen aan een voortgang; wacht tot het klaar is. Zie 4 ("Tijdens en na het laden"). |
| "In de zip staan meerdere leveringen" | In de zip (of in een zip in de zip) staan twee of meer leveringen. Pak de zip uit en kies de XML of de zip van één levering. |
| "VOLLEDIGHEIDSCONTROLE KLOPT NIET" | Werk met de levering zelf en meld het als issue (zonder de levering mee te sturen). |
| Een bolletje achter een kaart is rood | De bron van die kaart antwoordt nu niet, of anders dan VLEA verwacht; de uitleg bij het bolletje zegt welke bron en waarom. Laden mag je toch proberen. Probeer het later opnieuw (**Status vernieuwen**). Staan alle bolletjes rood, kijk dan of je internet hebt en of een proxy of firewall PDOK doorlaat. |

Het log staat in `%LOCALAPPDATA%\VLEA-AutoCAD\logs\` (één bestand per dag, 14 dagen). Mappen staan
er niet in, bestandsnamen wel. Id's en coördinaten uit een KLIC-levering komen er niet in (bij
niet-getekende objecten alleen klasse, thema en reden). Van `VKPUNTEN` komt er alleen een regel met aantallen in:
geen bestandsnaam, namen of coördinaten. Plak bij een foutmelding alleen het relevante
stuk, en haal eerst bestandsnamen en coördinaten weg die iets over een project zeggen.

## 13. Belangrijk
De kaarten zijn informatief. VLEA vervangt geen KLIC-melding: vraag vóór graafwerk altijd een
KLIC-melding aan.
Ook een levering die je met `VKKLIC` tekent, is informatief: de levering zelf blijft leidend bij
graafwerk.
