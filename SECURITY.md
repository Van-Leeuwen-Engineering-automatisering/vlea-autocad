# Beveiliging

## Een kwetsbaarheid melden
Meld een kwetsbaarheid **vertrouwelijk** via
[Report a vulnerability](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/security/advisories/new)
(tabblad **Security** van deze repository) of via https://vanleeuwenea.nl/contact, niet via een
openbaar issue.

Dit is een gratis project zonder beloningsregeling. We reageren zo snel als we kunnen, maar
garanderen geen termijn.

## Binnen scope
- De plugin, het installatieprogramma, de installatiescripts en de releasebestanden van deze
  repository.
- Buiten scope: PDOK, de BRO, de legger van Rijkswaterstaat, Digitaal Vlaanderen, DOV, AWV, de dienst van AHN5 en AHN6, de
  kaartdiensten van de gemeenten Eindhoven en Papendrecht, de kaartdiensten van de waterschappen De Stichtse Rijnlanden,
  Zuiderzeeland, Scheldestromen, Hunze en Aa's, Vechtstromen en Wetterskip Fryslân, GitHub en de kaartdata zelf, de website van
  VLEA, AutoCAD, en aangepaste versies van anderen.

## Wat de plugin doet en niet doet
- Netwerkverkeer alleen naar `api.pdok.nl` en `service.pdok.nl` (kaarten), `publiek.broservices.nl`
  (sonderingen en boringen: per register alleen zoeken en één object ophalen; peilbuizen: alleen de meetreeks van één
  filter als CSV), één vast pad van
  `geo.rijkswaterstaat.nl` (de legger van Rijkswaterstaat, voor de zones langs waterkeringen; uit te
  zetten), voor kaarten in een tekening in Vlaanderen (Lambert 72 of Lambert 2008) `geo.api.vlaanderen.be`
  (Digitaal Vlaanderen: alleen vier vaste adressen, voor het GRB als lijnen en vlakken en als kaartbeeld, de orthofoto
  en het hoogtemodel DHMV, ook voor `VKAHNPUNT` in een tekening in Lambert 72, en
  alleen met het stelsel van de tekening; een vraag in RD, zonder stelsel of met een datum weigert de plugin, omdat
  de dienst daar stil een verkeerd of leeg antwoord op geeft), voor de sonderingen in een
  tekening in Vlaanderen `www.dov.vlaanderen.be` (DOV, de Databank Ondergrond Vlaanderen: alleen de WFS met één
  volledige vraag per tegel en één sondering als XML, met als enige doorverwijzing die naar de export van dezelfde
  sondering), voor de hectometerpaaltjes in een tekening in Lambert 72
  `opendata.apps.mow.vlaanderen.be` (AWV, het Agentschap Wegen en Verkeer: alleen de WFS met de referentiepunten, in
  Lambert 72, zonder doorverwijzing; bij beide weigert de plugin een vraag zonder stelsel, met een
  filter of sortering of zonder vaste grens, omdat de dienst daar stil een verkeerd, leeg of afgekapt antwoord op geeft,
  en volgt hij nooit een link naar een volgende pagina), alleen als de gebruiker AHN5, AHN6 of de nieuwste kiest (de status
  van de bronnen alleen als bij het AHN-hoogtemodel een andere versie dan AHN4 staat, zie hieronder) `api.ellipsis-drive.com`
  (de dienst die het AHN daarvoor aanwijst: alleen zes vaste adressen, het hoogtemodel als WCS 1.0.0 in RD
  met hoogstens 2048 pixels per zijde, de bladwijzer met een vak in graden en een grens op het aantal; geen doorverwijzing,
  geen volgende pagina, geen filter), voor de riolering van de gemeenten waarvan PDOK geen riolering heeft `gisservice.eindhoven.nl`
  en `services8.arcgis.com` (de kaartdienst van de gemeente Eindhoven en die van de gemeente Papendrecht: alleen GET op de
  `query` van drie vaste lagen, met precies de parameters van de plugin: een rechthoek in RD binnen
  een vaste rechthoek om de gemeente, uitvoer in RD, een vaste volgorde, en een pagina die de plugin zelf in de vraag zet,
  hoogstens 15 pagina's van 2.000 objecten per laag en per tegel; geen doorverwijzing, geen link uit het antwoord, geen
  filter; alleen bij het laden van de riolering (`VKRIOOL`, `VKLADEN` of de knop Laden) met een gebied dat die rechthoek
  raakt, en niet als PDOK daar al riolering van die gemeente geeft), voor de zones langs waterkeringen van de zes waterschappen waarvan PDOK de zones niet of niet goed heeft
  `services1.arcgis.com`, `services.arcgis.com`, `geo.scheldestromen.nl` en `opendata.hunzeenaas.nl` (de kaartdiensten van De
  Stichtse Rijnlanden, Vechtstromen en Wetterskip Fryslân, van Zuiderzeeland, van Scheldestromen en van Hunze en Aa's, met
  dezelfde regel als de gemeenten, alleen op 14 vaste lagen: bij 13
  lagen alleen GET op de `query` van de laag, met precies dezelfde parameters als bij de gemeenten, binnen een vaste
  rechthoek om de data van die laag, hoogstens 15 pagina's van 2.000 objecten (bij Zuiderzeeland 1.000) per laag en per
  vraag; bij Hunze en Aa's alleen GET op de items van één vaste collectie (OGC API Features) met precies `f=json`, `crs` en
  `bbox-crs` in RD, een `bbox` binnen de rechthoek van de collectie en `limit` hoogstens 1.000, één pagina, nooit een
  volgende; geen doorverwijzing, geen link uit het antwoord, geen filter; alleen bij het laden van de zones
  (`VKZONERINGEN`, `VKLADEN` of de knop Laden) met een gebied dat de rechthoek van een laag raakt),
  `api.github.com`
  (versiecheck, uit te zetten) en, alleen als je `VKUPDATE` start (typen of
  de knop), `github.com` en `release-assets.githubusercontent.com` (de nieuwe versie downloaden). Geen
  telemetrie, geen account, geen sleutels, geen cookies.
- De status van de bronnen (het bolletje per kaart in het palet, en `VKSTATUS`) gebruikt alleen die bronnen: per
  kaart een of twee kleine verzoeken aan dezelfde dienst als de kaart, altijd in een vast testgebied en nooit in het
  gebied van de gebruiker. Het palet doet dat bij het openen hoogstens één keer per tien minuten (uit te zetten; de
  legger van Rijkswaterstaat alleen met de optie `rws` aan; Digitaal Vlaanderen, DOV en AWV alleen bij een tekening in
  Lambert 72 of Lambert 2008, zodat het palet bij een tekening in RD nooit iets aan `geo.api.vlaanderen.be`,
  `www.dov.vlaanderen.be` of `opendata.apps.mow.vlaanderen.be` vraagt; de dienst van AHN5 en AHN6 alleen als bij het
  AHN-hoogtemodel een andere versie dan AHN4 gekozen is).
  `VKSTATUS` vraagt altijd alle bronnen, ook de legger van Rijkswaterstaat, ook als de optie `rws` of "Status van de
  bronnen tonen" uit staat: het is een commando dat je zelf start. Ook Digitaal Vlaanderen, DOV en AWV vraagt
  `VKSTATUS` altijd, ook bij een tekening in RD. De dienst van AHN5 en AHN6 vraagt `VKSTATUS` niet: een getypt commando
  leest geen instellingen, en wie niets instelt maakt zo ook met `VKSTATUS` geen verbinding met `api.ellipsis-drive.com`.
  Die dienst vraagt alleen het palet, als bij het AHN-hoogtemodel een andere versie dan
  AHN4 gekozen is. Het palet en `VKSTATUS` vragen de kaartdiensten van de gemeenten (`gisservice.eindhoven.nl`,
  `services8.arcgis.com`) nooit: daar is geen proef voor (besluit van beheer, 12-11-2026); alleen het laden van de riolering
  vraagt ze. Het palet en `VKSTATUS` vragen de kaartdiensten van de waterschappen (`services1.arcgis.com`,
  `services.arcgis.com`, `geo.scheldestromen.nl`, `opendata.hunzeenaas.nl`) nooit: ook daar is geen proef voor (dezelfde
  keuze als bij de gemeenten); alleen het laden van de zones vraagt ze.
  Geen nieuwe bestemming, geen verzoek aan VLEA.
- `VKHELP` en `VKWEBSITE` (en in het palet de link en "?") openen alleen je eigen browser, met een van
  twee vaste adressen (de handleiding op `github.com` en de website `vanleeuwenea.nl`); de plugin maakt
  daarbij zelf geen verbinding en opent nooit een ander adres.
- `VKGOOGLE`, `VKSTREETVIEW`, `VKSTREETSMART` en `VKDINO` (en in palet en lint de knoppen onder "Bekijk de
  plek") openen je browser op de plek die je in de tekening aanwijst: Google Maps of Street View
  (`www.google.com`), StreetSmart van Cyclomedia (`streetsmart.cyclomedia.com`) of de kaart van
  DINOloket (`www.dinoloket.nl`), met de plek in het vaste fragment van het adres. De kern maakt het adres
  alleen uit de coördinaten (getallen, vaste host, pad en parameters), nooit uit tekst uit de tekening; vóór
  het openen moet het letterlijk op een van vier vaste sjablonen passen. Google, Cyclomedia en TNO (DINOloket) zien die plek (en wat
  hun pagina zelf laadt, zoals analysediensten). Bij DINOloket staat de plek achter het #-teken van het
  adres: dat deel stuurt je browser niet mee met het eerste verzoek, maar de pagina leest het en vraagt dan
  zelf de kaart voor die plek op bij TNO en de achtergrondkaart bij PDOK (`service.pdok.nl`); TNO en PDOK
  zien dus die plek. De plugin maakt daarbij zelf geen verbinding.
- Een ander programma starten doet de plugin op één plek, voor vijf doelen: het Google
  Earth-bestand openen (`VKKMZ`), de map met een nieuwe versie in Verkenner (`VKUPDATE`), een van die
  twee adressen in de browser, de plek in de browser volgens die sjablonen, en sinds 0.2.10 de kopie van een
  bijlage uit een KLIC-levering (`VKSCHETS`, `VKINFO`): alleen een pdf die VLEA zelf naar
  `%LOCALAPPDATA%\VLEA-AutoCAD\detail\` kopieerde, nooit een bestand in de levering of een plek die een tekening
  noemt; alleen in AutoCAD met schermen, nooit in de AutoCAD-kern zonder schermen.
  Geen opdrachtregel (cmd), geen script, geen PowerShell, geen installatie.
- `VKBIJLAGE` (sinds 1.2.0) start geen programma: AutoCAD leest de pdf zelf als onderlegger. Dat is nieuw: tot 1.2.0
  opende alleen je eigen pdf-lezer een bijlage, nu leest het AutoCAD-proces een pdf uit een levering. Daarom alleen een
  `.pdf` die via dezelfde harde toets in de levering gevonden is als bij `VKSCHETS` (nooit een plek die een tekening
  noemt buiten de levering, nooit een netwerkpad of een ander soort bestand), hoogstens 64 MB, eerst getoetst (de kop
  van een pdf, het einde, en geen versleuteling: VLEA plaatst geen beveiligde pdf), en als kopie naast de
  tekening (`<tekening>_kaarten`, submap `klic-bijlagen`), met een naam die VLEA zelf maakt. VLEA overschrijft en wist
  daar nooit een bestand. Voor de schaal leest VLEA zelf de papiermaat uit die kopie: alleen de kruisverwijzingen, de
  catalogus en de paginaboom (de maat, de draaiing en de eenheid van elke pagina), nooit de inhoud, en begrensd (een
  bestand van hoogstens 64 MB, een uitgepakte stroom van hoogstens 16 MB, hoogstens 500.000 objecten, 64 bijgewerkte
  versies, een paginaboom van hoogstens 32 niveaus en 2000 pagina's, en per pdf samen hoogstens 64 MB uit stromen,
  128 MB gelezen tekens en 2 miljoen waarden). Esc stopt ook het lezen van de maat. Een pdf die daar niet in past of niet
  te lezen is, geeft geen maat; dan vraagt VLEA om twee punten. Een beveiligde pdf leest VLEA ook zo niet.
- Instellingen, log en de versies die `VKUPDATE` ophaalt alleen in `%LOCALAPPDATA%\VLEA-AutoCAD\`.
- Geen automatische updater: `VKUPDATE` downloadt op jouw verzoek, controleert de SHA-256 tegen
  `SHA256SUMS.txt` van dezelfde release en pakt uit. Installeren doe je zelf met `Installeer.bat`;
  `VKUPDATE` start geen installatie, geen PowerShell en geen script.

## Wat het installatieprogramma doet en niet doet
`VLEA-AutoCAD-Setup.exe` doet hetzelfde als `Installeer.bat` en `Verwijder.bat`, met een venster.
- Het werkt alleen voor de gebruiker die het start en vraagt nooit beheerdersrechten (manifest
  `asInvoker`). Het schrijft op drie plekken: de map
  `%APPDATA%\Autodesk\ApplicationPlugins\VLEA-AutoCAD.bundle` (en tijdens het wisselen de mappen
  `VLEA-AutoCAD.nieuw` en `VLEA-AutoCAD.oud` ernaast), het register van de gebruiker onder
  `HKCU\Software\Autodesk\AutoCAD` (de waarde `TRUSTEDPATHS` per profiel; bij verwijderen ook de eigen
  registraties) en het logboek `%LOCALAPPDATA%\VLEA-AutoCAD\logs\setup.log` (zonder de naam van het
  Windows-account). Het register van de computer wordt alleen gelezen.
- Het maakt geen verbinding met internet, start geen ander programma en heeft geen opdrachtregelopties.
  De plugin zit in de exe zelf: precies de zip die ernaast wordt uitgegeven (de bouw weigert een exe
  met een andere zip). Uitpakken gebeurt alleen binnen de eigen map; een pakket met een
  pad daarbuiten wordt geweigerd.
- De exe is niet ondertekend, net als de DLL's van de plugin. Windows en je browser kunnen daarom
  waarschuwen, en Smart App Control van Windows 11 blokkeert hem. Controleer een download met
  `SHA256SUMS.txt`.

## Een download controleren
Naast elke release staat `SHA256SUMS.txt`, met een regel voor de zip en, vanaf versie 0.2.2, een voor
het installatieprogramma. `VKUPDATE` controleert de SHA-256 van de zip zelf; met de hand in PowerShell:
`Get-FileHash .\VLEA-AutoCAD.zip -Algorithm SHA256` of
`Get-FileHash .\VLEA-AutoCAD-Setup.exe -Algorithm SHA256`.

## Bekend restrisico: de vertrouwde map
Het installatieprogramma en `Installeer.bat` zetten de map
`%APPDATA%\Autodesk\ApplicationPlugins\VLEA-AutoCAD.bundle\Contents\<jaar>`
in de lijst vertrouwde locaties van AutoCAD (`TRUSTEDPATHS`). AutoCAD laadt DLL's uit die map
zonder te vragen. Die map staat in je eigen profiel: alles wat onder jouw Windows-account draait,
kan er een bestand neerzetten dat AutoCAD daarna zonder melding laadt. Dat risico hoort bij elke
installatie per gebruiker zonder beheerdersrechten.

Wat we ertegen doen:
- alleen precies de jaarmap van deze plugin wordt vertrouwd, niet de bovenliggende mappen;
- de knop Verwijderen van het installatieprogramma en `Verwijder.bat` halen die regel weer weg, en
  alleen die regel;

Installeer alleen het installatieprogramma en de zips van de releasepagina van deze repository.
