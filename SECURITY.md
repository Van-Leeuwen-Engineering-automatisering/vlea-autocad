# Beveiliging

## Een kwetsbaarheid melden
Meld een kwetsbaarheid **vertrouwelijk** via
[Report a vulnerability](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/security/advisories/new)
(tabblad **Security** van deze repository) of via info@vanleeuwenea.nl, niet via een
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
- Netwerkverkeer alleen naar `api.pdok.nl` en `service.pdok.nl` (kaarten en adres zoeken, ook de kaart en de luchtfoto in het kaartvenster van `VKZOEKKAART`), `publiek.broservices.nl`
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
  (versiecheck, één keer per dag, uit te zetten). Geen telemetrie, geen account, geen sleutels, geen cookies. De
  plugin downloadt geen programma's of updates (sinds 1.3.0; versies tot en met 1.2.0 downloaden bij `VKUPDATE` nog zelf van `github.com`
  en `release-assets.githubusercontent.com`, zie hieronder).
- Het kaartvenster (`VKZOEKKAART`, knop "Zoek op kaart", sinds 1.4.0) is een eigen venster zonder browsercomponent: elk
  stuk kaart (tegels van de BRT-achtergrondkaart), de luchtfoto en het zoeken komen via een eigen client met dezelfde
  regels als die van de kaarten, met een eigen limiet (hoogstens drie tegels tegelijk, 600 per minuut, 60 luchtfoto's per minuut), alleen naar
  `service.pdok.nl` en `api.pdok.nl`, en alleen in het geheugen (niets op schijf). De schermen halen zelf niets op: geen
  adres en geen browser. PDOK ziet welke stukken kaart je
  bekijkt, ook als je daarna niets kiest.
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
- `VKHELP`, `VKWEBSITE` en `VKUPDATE` (en in het palet de link, de "?", de regel "Nieuwe versie beschikbaar" en de
  link "Laat een review of wens achter", ook in "Over VLEA") openen alleen je eigen browser, met een van vier vaste
  adressen: de handleiding op `github.com`, de website `vanleeuwenea.nl`, en op de website de pagina
  `https://vanleeuwenea.nl/vlea-tool` bij het blok Bijwerken of bij Reviews en wensen. Het adres is letterlijk vast,
  zonder versienummer of andere gegevens; de plugin maakt daarbij zelf geen verbinding en opent nooit een ander adres. De website ziet dat bezoek en telt het, zoals bij elk bezoek.
  `VKUPDATE` opent de pagina alleen in AutoCAD met schermen en alleen als de bewaarde versiecheck een nieuwere versie
  kent; anders, en in de AutoCAD-kern, meldt het alleen de adressen.
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
- Een ander programma starten doet de plugin op één plek, voor vier doelen: het Google
  Earth-bestand openen (`VKKMZ`), een van die vier adressen in de browser, de plek in de browser volgens die
  sjablonen, en sinds 0.2.10 de kopie van een
  bijlage uit een KLIC-levering (`VKSCHETS`, `VKINFO`): alleen een pdf die VLEA zelf naar
  `%LOCALAPPDATA%\VLEA-AutoCAD\detail\` kopieerde, nooit een bestand in de levering of een plek die een tekening
  noemt; alleen in AutoCAD met schermen, nooit in de AutoCAD-kern zonder schermen.
  Geen opdrachtregel (cmd), geen script, geen PowerShell, geen installatie, en sinds 1.3.0 ook geen Verkenner.
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
- Instellingen en log alleen in `%LOCALAPPDATA%\VLEA-AutoCAD\`.
- Geen automatische updater: `VKUPDATE` opent alleen de pagina om bij te werken op de website (zie hierboven); de
  plugin downloadt en installeert niets. Bijwerken doe je zelf met het installatieprogramma van de website (of de zip).
  `VKUPDATE` start geen installatie, geen PowerShell en geen script.

## Wat de plugin wist
Sinds 1.3.0 wist de plugin bij het laden één eigen map: `%LOCALAPPDATA%\VLEA-AutoCAD\updates`, waarin versies tot en
met 1.2.0 een nieuwe versie klaarzetten. Eén keer per start, op
de achtergrond, stil, zonder netwerk en zonder een programma te starten; als er iets weg ging één regel in het
logboek, alleen met aantallen.
- Het pad komt nooit van buiten (geen instelling, register, bestand of argument). Het moet volledig zijn, geen
  netwerkpad, minstens drie mappen diep, en eindigen op letterlijk `VLEA-AutoCAD\updates`; anders gebeurt er niets.
- Alleen namen die VLEA daar zelf gaf: een map met een versienummer (`1.2.0`), zo'n map met `.deel` erachter (een
  afgebroken download), en de eigen tussennaam met `.weg` erachter; plus het bestand `bezig.slot`, alleen als gewoon
  bestand op naam weggehaald. Alles met een andere naam blijft staan, en dan ook de map `updates` zelf.
- Koppelingen (junction, symbolische koppeling of een ander verwijspunt van Windows): is `VLEA-AutoCAD`, `updates` of
  een naam daarin zelf een koppeling, dan blijft die staan en wordt hij niet geopend. Staat er in een versiemap ergens
  een koppeling, dan blijft die hele map staan. De plugin maakt zelf een lijst en wist van binnen naar buiten wat
  daarop staat; hij vraagt Windows nooit "wis deze map met alles erin", gaat nooit een koppeling in die er stond toen
  hij de lijst maakte, en vraagt vlak voor het wissen van elk item opnieuw of dat item een koppeling is. Vervangt iemand
  onder hetzelfde Windows-account tijdens het opruimen een map erboven door een koppeling, dan valt dat hierbuiten (zie
  verhoogde rechten hieronder).
- Een map wordt eerst hernoemd: dat lukt alleen als niemand hem gebruikt (bijvoorbeeld een open venster van
  `Installeer.bat`); lukt het niet, dan blijft alles staan tot de volgende start. Een alleen-lezen bestand, meer dan
  500 bestanden of meer dan 8 mappen diep: de map blijft staan.
- Draait AutoCAD met verhoogde rechten ("als administrator"), dan gebeurt er niets. Deze regels beschermen vooral
  tegen een ongeluk (een verhuisde map met een koppeling ervoor in de plaats); wie onder hetzelfde Windows-account
  draait, kan die bestanden ook zelf wissen.
- Verder wist de plugin uit zichzelf alleen losse bestanden die hij zelf maakte (oude logbestanden, kopieën van
  bijlagen, tijdelijke bestanden bij het opslaan, en een kaartbeeld dat hij zelf vervangt); geen andere map. Het
  installatieprogramma ruimt `updates` niet op.

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
- Staat er al een versie, dan zegt het venster welke en welke erbij komt; is het pakket in de exe ouder dan wat er
  staat, dan waarschuwt het (installeren mag dan nog wel: zo ga je terug naar een vorige versie).
- De exe is niet ondertekend, net als de DLL's van de plugin. Windows en je browser kunnen daarom
  waarschuwen, en Smart App Control van Windows 11 blokkeert hem. Controleer een download zoals hieronder.

## Versies tot en met 1.2.0
Wie nog 1.2.0 of ouder heeft, werkt één laatste keer bij zoals die versie dat doet: de regel "Nieuwe versie
beschikbaar" (of `VKUPDATE`) downloadt in AutoCAD de zip van de nieuwste release van `github.com` en
`release-assets.githubusercontent.com`, controleert de SHA-256 tegen `SHA256SUMS.txt`, pakt hem uit in
`%LOCALAPPDATA%\VLEA-AutoCAD\updates\<versie>\` en opent die map in Verkenner. De gebruiker start daarna zelf
`Installeer.bat`; dat start Windows PowerShell met `scripts\Installeer.ps1` en `-ExecutionPolicy Bypass`, in een
zichtbaar venster dat om J/N vraagt. Beveiligingssoftware kan dat melden: het hoort bij de oude versie. Vanaf 1.3.0
ruimt de plugin die map bij het starten van AutoCAD op (met de uitzonderingen onder "Wat de plugin wist"); bijwerken
loopt via de website. Daarom blijven de zip (met `Installeer.bat` en de
bundel in de wortel) en `SHA256SUMS.txt` (de zip op de eerste regel) in elke release, met dezelfde namen.

## Een download controleren
Wat de echtheid nu draagt: de releases in de openbare repository `vlea-autocad` op GitHub zijn **onveranderbaar**
(immutable releases): een uitgebracht bestand kan daar niet stil vervangen of gewist worden, ook niet door iemand met
schrijfrechten; die moet een nieuwe release maken. De downloadknoppen op https://vanleeuwenea.nl/vlea-tool wijzen naar
die releases. De plugin controleert een download niet meer zelf (hij downloadt geen programma's of updates), en de exe en de DLL's zijn niet
ondertekend.
- Met het programma `gh` van GitHub controleer je dat een gedownload bestand precies het bestand uit een release van
  deze repository is, ook als je het via de website kreeg:
  `gh release verify-asset v1.4.0 .\VLEA-AutoCAD-Setup.exe -R Van-Leeuwen-Engineering-automatisering/vlea-autocad`
  (en `gh release verify v1.4.0 -R Van-Leeuwen-Engineering-automatisering/vlea-autocad` voor de release zelf). Dat
  vangt een gewijzigde link of een beschadigde download, niet een kwaadwillende nieuwe release. `gh` vraagt eenmalig
  `gh auth login` (een gratis GitHub-account is genoeg); zonder account gebruik je `Get-FileHash` tegen
  `SHA256SUMS.txt` hieronder.
- Naast elke release staat `SHA256SUMS.txt`, met een regel voor de zip en, vanaf versie 0.2.2, een voor het
  installatieprogramma; met de hand in PowerShell: `Get-FileHash .\VLEA-AutoCAD.zip -Algorithm SHA256` of
  `Get-FileHash .\VLEA-AutoCAD-Setup.exe -Algorithm SHA256`.

## Bekende beperkingen voor ICT
- Geen stille installatie en geen opdrachtregelopties: het installatieprogramma installeert met een venster en een
  klik, per Windows-gebruiker. Tien pc's is tien keer klikken.
- Geen regel in "Apps en onderdelen" van Windows. Verwijderen kan met het installatieprogramma (knop Verwijderen) of
  met `Verwijder.bat` uit de zip, beide van https://vanleeuwenea.nl/vlea-tool; met de hand: de map
  `%APPDATA%\Autodesk\ApplicationPlugins\VLEA-AutoCAD.bundle` weghalen, in `TRUSTEDPATHS` van elk AutoCAD-profiel
  de regels `…\VLEA-AutoCAD.bundle\Contents\<jaar>` weghalen, en onder
  `HKCU\Software\Autodesk\AutoCAD\<versie>\<product>\Applications` de sleutels "VLEA AutoCAD <jaar>", "… Palet" en
  "… Civil" (zie ook README, Verwijderen). Instellingen en logboek staan in `%LOCALAPPDATA%\VLEA-AutoCAD`.
- Start een beheerder de exe onder zijn eigen account, dan komt de plugin in het profiel van de beheerder, niet van de
  gebruiker. Open het bestand onder het eigen Windows-account; bij bijwerken staat dan de zin "Op deze pc staat versie
  ..." in het venster.
- Zonder handtekening kan een beheerder het programma alleen per bestand toestaan (elke versie opnieuw), niet op
  uitgever.

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

Installeer alleen het installatieprogramma en de zips van de releasepagina van deze repository of van
https://vanleeuwenea.nl/vlea-tool (dezelfde bestanden).
