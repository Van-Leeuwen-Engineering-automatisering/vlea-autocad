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
- Buiten scope: PDOK, de BRO, de legger van Rijkswaterstaat, GitHub en de kaartdata zelf, de website van
  VLEA, AutoCAD, en aangepaste versies van anderen.

## Wat de plugin doet en niet doet
- Netwerkverkeer alleen naar `api.pdok.nl` en `service.pdok.nl` (kaarten), `publiek.broservices.nl`
  (sonderingen: alleen zoeken en één sondering ophalen,), één vast pad van
  `geo.rijkswaterstaat.nl` (de legger van Rijkswaterstaat, voor de zones langs waterkeringen; uit te
  zetten), `api.github.com` (versiecheck, uit te zetten) en, alleen als je `VKUPDATE` start (typen of
  de knop), `github.com` en `release-assets.githubusercontent.com` (de nieuwe versie downloaden). Geen
  telemetrie, geen account, geen sleutels, geen cookies.
- `VKHELP` en `VKWEBSITE` (en in het palet de link en "?") openen alleen je eigen browser, met een van
  twee vaste adressen (de handleiding op `github.com` en de website `vanleeuwenea.nl`); de plugin maakt
  daarbij zelf geen verbinding en opent nooit een ander adres.
- `VKGOOGLE`, `VKSTREETVIEW`, `VKSTREETSMART` en `VKDINO` (en in palet en lint de knoppen onder "Bekijk de
  plek") openen je browser op de plek die je in de tekening aanwijst: Google Maps of Street View
  (`www.google.com`), StreetSmart van Cyclomedia (`streetsmart.cyclomedia.com`) of de zoekpagina van
  DINOloket (`www.dinoloket.nl`). De kern maakt het adres alleen uit de coördinaten (getallen, vaste host,
  pad en parameters), nooit uit tekst uit de tekening; vóór het openen moet het letterlijk op een van vier
  vaste sjablonen passen. Google en Cyclomedia zien die plek (en wat hun pagina zelf laadt, zoals
  analysediensten); DINOloket krijgt geen coördinaten. De plugin maakt daarbij zelf geen verbinding.
- Een ander programma starten doet de plugin op één plek, voor vier doelen: het Google
  Earth-bestand openen (`VKKMZ`), de map met een nieuwe versie in Verkenner (`VKUPDATE`), een van die
  twee adressen in de browser en de plek in de browser volgens die sjablonen; alleen in AutoCAD met
  schermen, nooit in de AutoCAD-kern zonder schermen.
  Geen opdrachtregel (cmd), geen script, geen PowerShell, geen installatie.
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
  registraties) en het logboek `%LOCALAPPDATA%\VLEA-AutoCAD\logs\setup.log`. Het register van de
  computer wordt alleen gelezen.
- Het maakt geen verbinding met internet, start geen ander programma en heeft geen opdrachtregelopties.
  De plugin zit in de exe zelf: precies de zip die ernaast wordt uitgegeven (de bouw weigert een exe
  met een andere zip). Uitpakken gebeurt alleen binnen de eigen map; een pakket met een
  pad daarbuiten wordt geweigerd.
- De exe is niet ondertekend, net als de DLL's van de plugin. Windows en je browser kunnen daarom
  waarschuwen, en Smart App Control van Windows 11 blokkeert hem. Controleer een download met
  `SHA256SUMS.txt`.

## Een download controleren
Naast elke release staat `SHA256SUMS.txt`, met een regel voor de zip en een voor het
installatieprogramma. `VKUPDATE` controleert de SHA-256 van de zip zelf; met de hand in PowerShell:
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
