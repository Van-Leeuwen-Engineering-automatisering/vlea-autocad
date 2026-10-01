# Beveiliging

## Een kwetsbaarheid melden
Meld een kwetsbaarheid **vertrouwelijk** via
[Report a vulnerability](https://github.com/Van-Leeuwen-Engineering-automatisering/vlea-autocad/security/advisories/new)
(tabblad **Security** van deze repository) of via https://vanleeuwenea.nl/contact, niet via een
openbaar issue.

Dit is een gratis project zonder beloningsregeling. We reageren zo snel als we kunnen, maar
garanderen geen termijn.

## Binnen scope
- De plugin, de installatiescripts en de releasebestanden van deze repository.
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

## Een download controleren
Naast elke release staat `SHA256SUMS.txt`. `VKUPDATE` controleert de SHA-256 zelf; met de hand
in PowerShell: `Get-FileHash .\VLEA-AutoCAD.zip -Algorithm SHA256`.

## Bekend restrisico: de vertrouwde map
`Installeer.bat` zet de map `%APPDATA%\Autodesk\ApplicationPlugins\VLEA-AutoCAD.bundle\Contents\<jaar>`
in de lijst vertrouwde locaties van AutoCAD (`TRUSTEDPATHS`). AutoCAD laadt DLL's uit die map
zonder te vragen. Die map staat in je eigen profiel: alles wat onder jouw Windows-account draait,
kan er een bestand neerzetten dat AutoCAD daarna zonder melding laadt. Dat risico hoort bij elke
installatie per gebruiker zonder beheerdersrechten.

Wat we ertegen doen:
- alleen precies de jaarmap van deze plugin wordt vertrouwd, niet de bovenliggende mappen;
- `Verwijder.bat` haalt die regel weer weg, en alleen die regel;

Installeer alleen zips van de releasepagina van deze repository.
