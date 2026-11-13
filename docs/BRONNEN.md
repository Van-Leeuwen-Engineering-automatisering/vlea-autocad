# Bronnen van de kaarten

Dit bestand wordt gemaakt uit het bronregister van de plugin; bewerk het niet met de hand.

VLEA – kaarten voor AutoCAD haalt open data bij PDOK (api.pdok.nl en service.pdok.nl), voor de sonderingen, boringen en grondwaterstanden van peilbuizen bij de openbare uitgifte van de Basisregistratie Ondergrond (publiek.broservices.nl), voor de zones langs waterkeringen van Rijkswaterstaat uit de legger van Rijkswaterstaat (geo.rijkswaterstaat.nl) en, voor kaarten in een tekening in Vlaanderen, bij Digitaal Vlaanderen (geo.api.vlaanderen.be), voor de sonderingen bij de Databank Ondergrond Vlaanderen (www.dov.vlaanderen.be) en voor de hectometerpaaltjes bij het Agentschap Wegen en Verkeer (opendata.apps.mow.vlaanderen.be), en alleen als je AHN5, AHN6 of de nieuwste kiest bij de dienst die het AHN daarvoor aanwijst (api.ellipsis-drive.com), en voor de riolering in en bij Eindhoven en Papendrecht, die PDOK niet heeft, bij de kaartdienst van de gemeente (gisservice.eindhoven.nl en services8.arcgis.com): van Eindhoven open data, van Papendrecht openbaar gedeelde data zonder genoemde licentie, en voor de zones langs waterkeringen van De Stichtse Rijnlanden, Zuiderzeeland, Scheldestromen, Hunze en Aa's, Vechtstromen en Wetterskip Fryslân, die PDOK niet of niet goed heeft, bij de kaartdienst van het waterschap (services1.arcgis.com, services.arcgis.com, geo.scheldestromen.nl en opendata.hunzeenaas.nl): van De Stichtse Rijnlanden en Hunze en Aa's open data, van Zuiderzeeland data zonder gebruiksbeperking, van Scheldestromen, Vechtstromen en Wetterskip Fryslân openbaar gedeelde data zonder genoemde licentie. De data is van de bronhouders hieronder; die riolering is van de gemeente zelf: Gemeente Eindhoven (Riolering en aansluitingen), Public Domain Mark 1.0 (https://creativecommons.org/publicdomain/mark/1.0/deed.nl), en Gemeente Papendrecht (Rioolviewer Papendrecht), openbaar gedeeld, geen licentie genoemd; die zones zijn van het waterschap zelf: Hoogheemraadschap De Stichtse Rijnlanden (Waterschapsverordening), CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/deed.nl); Waterschap Zuiderzeeland (Zonering waterkering), geen gebruiksbeperking; Waterschap Scheldestromen (zoneringen waterkeringen), openbaar gedeeld, geen licentie genoemd; Waterschap Hunze en Aa's (Zonering waterkering), Public Domain Mark 1.0 (https://creativecommons.org/publicdomain/mark/1.0/deed.nl); Waterschap Vechtstromen (legger, vastgesteld), openbaar gedeeld, geen licentie genoemd; en Wetterskip Fryslân (Waterkering, open data), openbaar gedeeld, geen licentie genoemd. VLEA neemt een uitsnede van het gekozen gebied en zet die om naar AutoCAD-objecten op NLCS-lagen: de data wordt dus bewerkt.

VLEA zet per kaart een bronvermelding op de opdrachtregel, onderaan het palet en in de tekeningeigenschappen ("Bronvermelding <kaart>"); `VKINFO` noemt haar bij een object, behalve bij het AHN-hoogtemodel, het DHMV, de BRT, de riolering en de zones langs waterkeringen (daar hangt ze af van wat je precies laadde). Als tekst onder het gebied komt ze alleen als je in de instellingen **Bronvermelding in de tekening** aanzet (sinds 1.1.0 standaard uit; getypt `bronvermelding=aan`). **Sommige bronnen vragen om naamsvermelding als je een tekening deelt of publiceert: neem de bronvermelding dan over of zet die keuze aan.**

| Kaart | Commando | Bronhouder | Licentie |
|---|---|---|---|
| AHN hoogtemodel | VKAHN | Actueel Hoogtebestand Nederland | [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/deed.nl) |
| BAG (panden en adressen) | VKBAG | Kadaster | [Public Domain Mark 1.0](https://creativecommons.org/publicdomain/mark/1.0/deed.nl) |
| BGT (topografie) | VKBGT | Kadaster | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.nl) |
| BGT als kaartbeeld | VKBGTBEELD | Kadaster | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.nl) |
| Boringen (BRO) | VKBORINGEN | TNO Geologische Dienst Nederland | [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/deed.nl) |
| BRT (topografische kaart) | VKBRT | Kadaster | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.nl) |
| DHMV hoogtemodel (Vlaanderen) | VKDHMV | Digitaal Vlaanderen | [Modellicentie Gratis Hergebruik v1.0](https://data.vlaanderen.be/id/licentie/modellicentie-gratis-hergebruik/v1.0) |
| GRB (topografie Vlaanderen) | VKGRB | Digitaal Vlaanderen | [Modellicentie Gratis Hergebruik v1.0](https://data.vlaanderen.be/id/licentie/modellicentie-gratis-hergebruik/v1.0) |
| GRB als kaartbeeld | VKGRBBEELD | Digitaal Vlaanderen | [Modellicentie Gratis Hergebruik v1.0](https://data.vlaanderen.be/id/licentie/modellicentie-gratis-hergebruik/v1.0) |
| Kadastrale kaart | VKKADASTER | Kadaster | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.nl) |
| Luchtfoto | VKLUCHTFOTO | Beeldmateriaal.nl | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.nl) |
| Natura 2000 | VKNATURA2000 | Ministerie van Landbouw, Natuur en Voedselkwaliteit | [Public Domain Mark 1.0](https://creativecommons.org/publicdomain/mark/1.0/deed.nl) |
| Wegen en hectometrering (NWB) | VKNWB | Rijkswaterstaat | [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/deed.nl) |
| Orthofoto Vlaanderen | VKORTHO | Digitaal Vlaanderen | [Modellicentie Gratis Hergebruik v1.0](https://data.vlaanderen.be/id/licentie/modellicentie-gratis-hergebruik/v1.0) |
| Peilbuizen (BRO) | VKPEILBUIZEN | TNO Geologische Dienst Nederland | [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/deed.nl) |
| Hectometerpaaltjes (AWV) | VKREFPUNTEN | Agentschap Wegen en Verkeer | [Modellicentie Gratis Hergebruik v1.0](https://data.vlaanderen.be/id/licentie/modellicentie-gratis-hergebruik/v1.0) |
| Riolering gemeente (GWSW) | VKRIOOL | Stichting RIONED | [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/deed.nl) |
| Sonderingen (BRO) | VKSONDERINGEN | TNO Geologische Dienst Nederland | [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/deed.nl) |
| Sonderingen (DOV) | VKSONDERINGENDOV | Databank Ondergrond Vlaanderen (MOW, Afdeling Geotechniek) | [Modellicentie Gratis Hergebruik v1.0](https://data.vlaanderen.be/id/licentie/modellicentie-gratis-hergebruik/v1.0) |
| Spoorwegen (ProRail) | VKSPOOR | ProRail | [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/deed.nl) |
| Zones langs waterkeringen | VKZONERINGEN | Het Waterschapshuis en Rijkswaterstaat | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.nl) |

Kies je bij AHN hoogtemodel of bij de hoogte op een punt AHN5 of AHN6, dan komen die van de dienst die het AHN daarvoor aanwijst (api.ellipsis-drive.com). Bronhouder is ook dan het Actueel Hoogtebestand Nederland (uitgevoerd door Het Waterschapshuis). Het AHN noemt voor AHN5 en AHN6 geen licentie bij naam; het zegt: "De overheid heeft het AHN volledig en zonder enige voorwaarden openbaar gedeeld in de vorm van open data, om hergebruik van de beschikbare gegevens te stimuleren." (https://www.ahn.nl/over-het-programma-ahn). De bronvermelding zegt dan "open data, zonder voorwaarden gedeeld", met die pagina.

Adressen zoeken gaat via de PDOK Locatieserver.

Laagnamen en lijntypen: NLCS 5.0.2 van digiGO, CC BY 4.0; omgezet naar JSON, laagkeuze VLEA.

Informatief; vervangt geen KLIC-melding.
