# VLEA – kaarten voor AutoCAD

Gratis plugin voor AutoCAD die open kaarten van [PDOK](https://www.pdok.nl) in je tekening zet: in
RD-coördinaten (meters), op NLCS-lagen, met bronvermelding. Zonder account, zonder eigen server:
de plugin haalt de kaarten rechtstreeks bij PDOK op (de sonderingen bij de openbare uitgifte van de
Basisregistratie Ondergrond, de zones van Rijkswaterstaat uit de legger van Rijkswaterstaat).

> **Downloaden:** [VLEA-AutoCAD-Setup.exe](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/releases/latest/download/VLEA-AutoCAD-Setup.exe), het
> installatieprogramma van de nieuwste versie, voor AutoCAD 2025, 2026 en 2027. Liever de zip met
> `Installeer.bat`: [VLEA-AutoCAD.zip](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/releases/latest/download/VLEA-AutoCAD.zip). Wat er per
> versie veranderd is, staat bij de [releases](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/releases). De handleiding staat in
> [`docs/handleiding.md`](docs/handleiding.md). Meer over de plugin: https://vanleeuwenea.nl/autocad-kaarten.

## Wat kan het (versie 0.2)

| Onderdeel | Commando | Wat |
|---|---|---|
| Palet | `VKPALET` | Palet openen of sluiten. Alles kan ook vanuit het palet: per kaart een knop "Laden", een rij knoppen voor het gereedschap en een link naar de website. De keuzes per kaart en per gereedschap staan in het instellingenvenster (tandwiel), aan/uit standaard aan. |
| Gebied | `VKADRES`, `VKGEBIED` | Adres, postcode of perceel zoeken; rechthoek, gesloten polylijn of coördinaten als gebied kiezen. |
| | `VKCONTOUR` | Een strook op een vaste breedte langs een lijn (in Civil 3D ook een as) tekenen en als gebied kiezen. |
| Laden | `VKLADEN` | Kaarten laden voor het gekozen gebied, ook meer tegelijk (sleutels met komma's, bijvoorbeeld `bgt,bag`). In het palet heeft elke kaart een eigen knop "Laden". |
| Ondergrond | `VKBGT` | BGT (actuele versie), in groepen: wegen, water, panden, terrein, namen en nummers, overig. |
| | `VKBAG` | BAG-panden en, als optie, de adressen met huisnummer (alleen actuele objecten; de rest wordt gemeld). |
| | `VKBRT` | BRT-topografie voor een groter gebied (beta): vector (TOP10NL) of het kaartbeeld van de achtergrondkaart. |
| | `VKKADASTER` | Kadastrale grenzen en perceelnummers. |
| | `VKLUCHTFOTO` | Luchtfoto, "snel" (25 cm) of "scherp" (8 cm). |
| Hoogte | `VKAHN` | AHN-maaiveld (of oppervlak met gebouwen) als surface, één per gebied ("VLEA AHN RD 154750-462750 500x500"). **Alleen in Civil 3D**; in AutoCAD zonder Civil 3D staat AHN in het palet grijs. |
| | `VKAHNPUNT` | AHN-hoogte op aangewezen punten: een punt op die hoogte en een label "NAP +4,98 m". Ook zonder Civil 3D. |
| Grondonderzoek | `VKSONDERINGEN` | Sonderingen uit de BRO met label en, per sondering, een sondeerplot naast de kaart (beta). |
| Infra | `VKNWB` | Wegassen en hectometrering (Nationaal Wegenbestand). |
| | `VKSPOOR` | Sporen, wissels, kilometrering, overwegen (beta). |
| | `VKRIOOL` | Gemeentelijke riolering. Gedeeltelijke dekking; niet voor WIBON/KLIC. |
| Natuur | `VKNATURA2000` | Natura 2000-gebieden (beta). |
| Beperkingen | `VKZONERINGEN` | Zones langs waterkeringen: kernzone, beschermingszone en profiel van vrije ruimte (beta). Niet elk waterschap levert zijn zones aan; een ontbrekende zone betekent niet dat er geen zone is; de legger van de beheerder is leidend. |
| KLIC | `VKKLIC` | Een KLIC-levering (de IMKL-XML of de zip van het Kadaster) inlezen en op NLCS-lagen tekenen, met een telling per thema en bij elk object dat niet getekend kan worden de reden. Opnieuw inlezen gaat per meldnummer: een andere levering wordt nooit gewist. Werkt zonder internet. |
| Google Earth | `VKKMZ`, `VKKMLIMPORT` | Objecten als KMZ (en standaard ook als los .kml-bestand) naar Google Earth (één open lijn: boortracé met begin, eind en lengte; Enter = alle VLEA-kaarten in het gebied, zonder KLIC-levering); een KML of KMZ inlezen op vaste lagen. |
| Bekijk de plek | `VKGOOGLE`, `VKSTREETVIEW`, `VKSTREETSMART`, `VKDINO` | Een punt aanwijzen (Enter = midden van het beeld) en die plek in je browser openen: Google Maps met een speld, Street View (het dichtstbijzijnde panorama; met een tweede punt ook de kijkrichting), StreetSmart van Cyclomedia (daarvoor heb je een eigen account van Cyclomedia nodig) of DINOloket. DINOloket kent geen link naar een plek: het opent de zoekpagina en de coördinaten om te zoeken staan op de opdrachtregel. In het palet en op het lint: "Bekijk de plek". |
| Gereedschap | `VKINFO`, `VKWISSEN`, `VKSTIJL`, `VKOVER` | Gegevens van een object, eigen imports wissen, NLCS-kleuren of grijze onderlegger, versie, commando's en licenties. |
| Hulp | `VKHELP`, `VKWEBSITE` | Versie, installatiemap, map van instellingen en logboek, bijwerken; de handleiding of de website van VLEA in je browser. |
| Bijwerken | `VKUPDATE` | Nieuwste versie ophalen, controleren (SHA-256) en uitgepakt klaarzetten. Installeren doe je zelf met `Installeer.bat` (of met het installatieprogramma van de nieuwe versie). |

Alle commando's beginnen met `VK` en werken ook vanaf de opdrachtregel en in scripts, ook de
kaartcommando's (`VKBGT` enz.) in de AutoCAD-kern zonder schermen.

Ligt er in het gekozen gebied niets van een kaart, dan zegt VLEA dat in een zin (bijvoorbeeld "Er ligt
geen sondering uit de BRO binnen dit gebied.") in plaats van "0 objecten".

**Niet in versie 0.2:** DTB (PDOK stopt ermee op 31-12-2026) en waterschapsriolering.

### Laagnamen

- BGT en riolering volgen de officiële NLCS 5.0-mappings van digiGO.
- Kadaster, BAG, BRT, wegen, spoor, AHN, Natura 2000, sonderingen en de zones langs waterkeringen
  hebben geen officiële mapping; daar kiest VLEA een laag uit de NLCS-objectentabellen.
- De luchtfoto en het kaartbeeld van de BRT staan op een eigen laag (NLCS kent geen rasterlaag),
  de contour van `VKCONTOUR` ook (`VLEA-KAART-GEBIED`: een laadgebied, geen object).
- KLIC heeft geen officiële NLCS-mapping; VLEA kiest per thema (laagspanning, gas, water, riool …)
  lagen uit de NLCS-objectentabellen (discipline OI) en maakt alleen voor het thema "overig" een
  eigen object (`OVERIG`) volgens de NLCS-systematiek.
- VLEA tekent op NLCS-lagen; de tool is niet door digiGO gecertificeerd.
- Lijntypen gebruiken `NLCS.shx`. Stuur je een tekening naar iemand zonder deze plugin, gebruik dan
  eTransmit zodat `NLCS.shx` meegaat.

## Systeemeisen

- Windows 10 of 11, 64-bit.
- AutoCAD **2025**, **2026** of **2027** voor Windows, of een product op AutoCAD-basis (bijvoorbeeld
  Civil 3D of Map 3D). In de download zit voor elk jaar een eigen build; AutoCAD laadt die van zijn
  eigen jaar:

  | AutoCAD | Map in de bundel | Opmerking |
  |---|---|---|
  | 2025 | `Contents\2025` | |
  | 2026 | `Contents\2026` | |
  | 2027 | `Contents\2027` | nieuw in versie 0.2 (AutoCAD 2027 draait op .NET 10) |

- **Niet** voor AutoCAD LT, AutoCAD voor Mac of AutoCAD Web: die kunnen deze plugin niet laden (het is
  een .NET-plugin voor AutoCAD voor Windows; AutoCAD LT laadt geen .NET-plugins).
- Internetverbinding naar `api.pdok.nl` en `service.pdok.nl`; voor de sonderingen naar
  `publiek.broservices.nl` (de openbare uitgifte van de Basisregistratie Ondergrond); voor de zones
  langs waterkeringen van Rijkswaterstaat naar `geo.rijkswaterstaat.nl` (uit te zetten met de optie
  `rws`); voor `VKUPDATE` ook naar GitHub (zie [Privacy](#privacy)). `VKKLIC` heeft geen internet nodig.
  `VKHELP`, `VKWEBSITE` en de commando's onder "Bekijk de plek" openen je eigen browser.
- De tekening staat in meters (RD). Een tekening in een andere eenheid weigert VLEA, zonder iets
  te tekenen.

## Installeren

### Met het installatieprogramma

1. Download `VLEA-AutoCAD-Setup.exe` bij de
   [nieuwste release](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/releases/latest).
2. Sluit AutoCAD en open het bestand. Het programma is niet ondertekend: **je browser en Windows kunnen
   waarschuwen**. Kies in je browser dat je het bestand wilt behouden, en in Windows **Meer informatie**
   en daarna **Toch uitvoeren**, als je de download vertrouwt (zie
   [Download controleren](#download-controleren)).
3. Het venster zegt wat het gaat doen en welke AutoCAD het vond. Klik op **Installeren**. Het programma
   doet hetzelfde als `Installeer.bat` hieronder, voor jouw Windows-account en zonder beheerdersrechten:
   het zet de plugin in `%APPDATA%\Autodesk\ApplicationPlugins\VLEA-AutoCAD.bundle` en zet voor elke
   AutoCAD-versie alleen de map met de DLL's (`…\VLEA-AutoCAD.bundle\Contents\2025`, `…\Contents\2026`
   of `…\Contents\2027`) in de lijst vertrouwde locaties van AutoCAD (`TRUSTEDPATHS`), niet de map
   `ApplicationPlugins` zelf (zie [`SECURITY.md`](SECURITY.md)). Het maakt geen verbinding met internet.
4. Start AutoCAD. Vraagt AutoCAD of de plugin geladen mag worden, kies **Load** of **Load Once**
   (AutoCAD heeft geen Nederlandse versie). De DLL's van VLEA zijn niet ondertekend; het venster heet dan
   "Security - Unsigned Executable File", met Always Load, Load Once en Do Not Load. Het kan ook
   "File Loading - Security Concern" zijn, met de knop Load.
5. Het palet opent de eerste keer vanzelf. Daarna: typ `VKPALET` of gebruik het lint-tabblad **VLEA**.

Draait AutoCAD nog, dan zegt het programma dat en wijzigt het niets. Meldt het dat er nog geen
AutoCAD-profiel is: start AutoCAD één keer, sluit het en installeer opnieuw.

Staat op je pc **Smart App Control** van Windows 11 aan, dan blokkeert Windows niet-ondertekende
programma's en scripts van internet, zonder knop om door te gaan: het installatieprogramma start dan
niet, en `Installeer.bat` uit de zip ook niet.

### Met de zip en `Installeer.bat`

Dezelfde installatie als script: je ziet elke stap in een venster met tekst.

1. Download `VLEA-AutoCAD.zip` bij de
   [nieuwste release](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/releases/latest)
   en pak de zip helemaal uit (rechtsklik, **Alles uitpakken**). Start niets vanuit de zip.
2. Sluit AutoCAD.
3. Dubbelklik `Installeer.bat`. **Windows kan waarschuwen** dat het bestand van internet komt; kies
   dan **Meer informatie** en daarna **Toch uitvoeren** als je de download vertrouwt (zie
   [Download controleren](#download-controleren)). Het script zegt wat het gaat doen en vraagt
   `Doorgaan? (J/N)`: typ J en druk op Enter. Het doet daarna wat bij stap 3 hierboven staat.
4. Start AutoCAD; verder zoals stap 4 en 5 hierboven.

Meldt het script "0 profielen": start AutoCAD één keer, sluit het en draai `Installeer.bat` opnieuw.

### Verwijderen

Sluit AutoCAD en open `VLEA-AutoCAD-Setup.exe` opnieuw: staat VLEA op de pc, dan heeft het venster de
knop **Verwijderen**. Of dubbelklik `Verwijder.bat` uit de zip; het script vraagt
`VLEA verwijderen uit AutoCAD 2025, 2026 en 2027? (J/N)`. Beide halen, voor jouw Windows-gebruiker, weg:
de map `%APPDATA%\Autodesk\ApplicationPlugins\VLEA-AutoCAD.bundle`, de registraties die AutoCAD voor
VLEA aanmaakte ("VLEA AutoCAD <jaar>", "… Palet" en "… Civil") en in `TRUSTEDPATHS`, in elk profiel,
precies de regels van VLEA (`…\VLEA-AutoCAD.bundle\Contents\2025`, `…\Contents\2026` en
`…\Contents\2027`). Andere plugins en regels blijven staan. Je instellingen, het logboek en de versies
die `VKUPDATE` ophaalde, in `%LOCALAPPDATA%\VLEA-AutoCAD\`, blijven ook staan; wil je die ook weg, typ
dan in een opdrachtprompt, in de uitgepakte map, `Verwijder.bat -OokInstellingen`.

### Bijwerken

Typ `VKUPDATE` in AutoCAD. VLEA vraagt bij GitHub wat de nieuwste versie is, downloadt
die, controleert de SHA-256 tegen `SHA256SUMS.txt` en zet hem uitgepakt klaar in
`%LOCALAPPDATA%\VLEA-AutoCAD\updates\<versie>\` (in AutoCAD opent die map in Verkenner). Sluit daarna
AutoCAD en dubbelklik `Installeer.bat` in die map. VLEA installeert nooit zelf en start geen scripts.
Nog geen release of al de nieuwste versie: `VKUPDATE` zegt dat en downloadt niets.

Je kunt ook het installatieprogramma van de nieuwe versie downloaden en openen: het vervangt de versie
die er staat.

### Download controleren

Naast de downloads staat `SHA256SUMS.txt`, met een regel voor de zip en een voor het
installatieprogramma (`VKUPDATE` controleert de zip zelf). Vergelijk in PowerShell:

```powershell
Get-FileHash .\VLEA-AutoCAD-Setup.exe -Algorithm SHA256
Get-FileHash .\VLEA-AutoCAD.zip -Algorithm SHA256
```

## Privacy

De plugin stuurt niets naar VLEA en verzamelt geen gebruiksgegevens: geen account, geen telemetrie,
geen sleutels. Hij maakt alleen deze verbindingen, allemaal via https:

| Wanneer | Met | Wat gaat er mee |
|---|---|---|
| Kaarten laden, adres zoeken | PDOK: `api.pdok.nl`, `service.pdok.nl` | het gebied of de zoektekst, en de versie van de plugin |
| Sonderingen laden | BRO: `publiek.broservices.nl` (alleen zoeken en één sondering ophalen) | het gebied (als zoekvak in graden), en de versie van de plugin |
| Zones langs waterkeringen laden, met de optie `rws` (standaard aan) | Rijkswaterstaat: `geo.rijkswaterstaat.nl` (alleen de openbare legger) | het gebied, en de versie van de plugin |
| Eén keer per dag (uit te zetten in de instellingen van het palet, onder "Algemeen") | GitHub: `api.github.com` | alleen de versie van de plugin |
| Alleen als je `VKUPDATE` start (typen, de knop Bijwerken in het palet of op het lint, of de regel "Nieuwe versie beschikbaar" onderaan het palet) | GitHub: `api.github.com`, `github.com` en `release-assets.githubusercontent.com` (daar laat GitHub de downloads vandaan komen) | alleen de versie van de plugin |
| Alleen als je `VKHELP` of `VKWEBSITE` typt, Help op het lint kiest, of in het palet de link vanleeuwenea.nl of de knop "?" gebruikt | je eigen browser opent de handleiding op `github.com` of de website `vanleeuwenea.nl`; de plugin maakt zelf geen verbinding | wat je browser altijd meestuurt; de plugin geeft alleen het vaste adres door |
| Alleen als je `VKGOOGLE`, `VKSTREETVIEW` of `VKSTREETSMART` start (typen, of de knoppen onder "Bekijk de plek" in het palet en op het lint) | je eigen browser opent Google Maps of Street View (`www.google.com`) of StreetSmart van Cyclomedia (`streetsmart.cyclomedia.com`); de plugin maakt zelf geen verbinding | de coördinaten van het gekozen punt (bij Street View ook de kijkrichting): die dienst ziet die plek (en wat de pagina van die dienst zelf laadt, zoals analysediensten), dus waar je project ligt; plus wat je browser altijd meestuurt (bij Google ook je Google-account als je daar ingelogd bent, bij StreetSmart je account van Cyclomedia) |
| Alleen als je `VKDINO` start (typen, of de knop DINOloket) | je eigen browser opent de zoekpagina van DINOloket (`www.dinoloket.nl`); de plugin maakt zelf geen verbinding | geen coördinaten: die staan op de opdrachtregel en je zoekt er zelf mee; wat je browser altijd meestuurt |
| Na `VKKMZ`, als Google Earth het bestand opent (alleen in AutoCAD met schermen) | Google Earth zelf, niet de plugin: het haalt kaartbeelden bij Google op voor het gebied in het bestand | wat Google Earth meestuurt (zie de voorwaarden van Google); de plugin stuurt niets |

Bij elke verbinding ziet de ontvanger je IP-adres. Cookies bewaart en stuurt de plugin niet. Een
doorverwijzing naar een adres buiten deze lijst volgt de plugin niet. Een ander programma start de
plugin alleen voor vier dingen: het Google Earth-bestand openen (`VKKMZ`), de map met de nieuwe versie
tonen (`VKUPDATE`), een van de twee vaste adressen hierboven in je browser (`VKHELP`, `VKWEBSITE`, en
de link en "?" in het palet) en de plek in je browser (`VKGOOGLE`, `VKSTREETVIEW`, `VKSTREETSMART`,
`VKDINO`: een adres volgens een vast sjabloon met alleen de coördinaten van het gekozen punt); alleen in
AutoCAD met schermen. Instellingen, het logbestand en de versies
die `VKUPDATE` ophaalt, staan alleen op je eigen pc, in `%LOCALAPPDATA%\VLEA-AutoCAD\`.

Een KLIC-levering leest VLEA alleen van je eigen schijf; er gaat niets van naar buiten. In het logboek
komen geen id's of coördinaten uit de levering.
De contactvelden uit de levering (contactpersoon, naam, telefoon, e-mail, adres, aanvrager en
opdrachtgever) neemt VLEA niet over; een e-mailadres in een vrij tekstveld wordt weggelaten. Wat een
netbeheerder in een vrije tekst of een label zet, komt verder ongewijzigd mee in de tekening (bij
`VKINFO` en, bij een label, als tekst).

## Bronnen en licenties van de kaarten

De data is van de bronhouders; PDOK stelt haar beschikbaar (de sonderingen de BRO, de zones van
Rijkswaterstaat de legger van Rijkswaterstaat). Bij CC BY-bronnen is naamsvermelding
verplicht: VLEA zet de bronvermelding in de tekeningeigenschappen en kan haar als tekst in de
tekening plaatsen. **Neem de bronvermelding over op tekeningen die je deelt of publiceert.**

Per kaart de bronhouder en de licentie: zie [`docs/BRONNEN.md`](docs/BRONNEN.md). Dat bestand
wordt gemaakt uit het bronregister in de code (een test bewaakt dat), zit als `BRONNEN.md` in de zip
en `VKOVER` toont dezelfde gegevens. Adressen zoeken gaat via de PDOK Locatieserver.

In het kort, wat de licenties vragen als je een tekening of export met de kaartdata deelt:

| Licentie | Kaarten | Wat het betekent voor wie de data verder verspreidt |
|---|---|---|
| CC0 1.0, Public Domain Mark 1.0 | AHN, NWB, spoor, riolering, sonderingen, Natura 2000, BAG | geen voorwaarden; een bronvermelding is netjes, maar niet verplicht |
| CC BY 4.0 | BGT, BRT, kadaster, luchtfoto | naam van de bronhouder en de licentie noemen, en zeggen dat de data bewerkt is: de bronvermelding van VLEA doet dat |
| **CC BY-SA 4.0** ("gelijk delen") | de **zones langs waterkeringen** (`VKZONERINGEN`): Het Waterschapshuis en Rijkswaterstaat | als bij CC BY, en daarbij: wie de zones (of een bewerking ervan, bijvoorbeeld de uitgesneden zones in een DWG, KMZ of export) verder verspreidt, moet die bewerking onder dezelfde of een compatibele licentie delen en mag er geen extra beperkingen op leggen. De licentie spreekt van delen met het publiek; of een tekening aan één opdrachtgever daaronder valt, beoordeelt VLEA niet. Of het ook voor de rest van een tekening geldt, hangt af van hoe de zones erin gebruikt zijn; ook daarover geeft VLEA geen juridisch oordeel. Wil je dat vermijden, deel de zones dan niet mee: wis ze in de kopie die je verstuurt (`VKWISSEN`, kaart `zoneringen`). Een bevroren of uitgezette laag zit nog in het bestand. |

Voor de zones houdt VLEA de strengste licentie van de twee aan: de zones van de waterschappen zijn
CC BY-SA 4.0, de legger van Rijkswaterstaat is CC0 1.0. De bronvermelding, `BRONNEN.md` en `VKOVER`
noemen daarom voor de hele kaart CC BY-SA 4.0.

Een **KLIC-levering** (`VKKLIC`) is geen open data maar een levering volgens de WIBON, en
**vertrouwelijk** (WIBON art. 4 lid 2): je mag de gegevens alleen aan anderen geven voor zover dat
noodzakelijk is om graafschade te voorkomen, of voor de oriëntatie op een verzoek tot medegebruik of
coördinatie. Dat geldt ook voor een tekening, export of Google Earth-bestand met de levering erin; de
bronvermelding van VLEA zegt daarom "(WIBON, vertrouwelijk)", en `VKKMZ` neemt KLIC met Enter niet mee.

De exacte voorwaarden staan in de licentieteksten (de link staat bij elke kaart in `BRONNEN.md`).

**Belangrijk:** de kaarten zijn informatief. VLEA **vervangt geen KLIC-melding**; vraag vóór
graafwerk altijd een KLIC-melding aan. De riolering is onvolledig en niet bedoeld voor WIBON of KLIC.
Ook een levering die je met `VKKLIC` tekent, is informatief: de levering zelf blijft leidend bij
graafwerk.

## Licentie

- De plugin is gratis te gebruiken, ook voor je werk. Wijzigen, terugvertalen en zelf verspreiden
  mogen niet. Zie [`LICENSE`](LICENSE). De broncode is niet openbaar.
- Naam en logo van VLEA: zie [`TRADEMARK.md`](TRADEMARK.md).
- De NLCS-bestanden in de zip (laagnamen en lijntypen, digiGO NLCS 5.0.2) vallen onder CC BY 4.0; zie
  `LICENSE-CC-BY-4.0.txt` en `NOTICE-NLCS.txt` in de zip.
- AutoCAD en Civil 3D zijn merken van Autodesk. VLEA is een onafhankelijke uitbreiding.

## Vragen en fouten

- Vragen en fouten: via [Issues](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/issues).
  Voeg geen tekeningen of projectgegevens toe. De tool is gratis en zonder garantie of gegarandeerde
  ondersteuning.
- Een beveiligingsprobleem: zie [`SECURITY.md`](SECURITY.md).
- Handleiding: [`docs/handleiding.md`](docs/handleiding.md).
