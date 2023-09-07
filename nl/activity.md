---
title: Lidarr Activiteit
description: 
published: true
date: 2022-02-06T09:06:39.366Z
tags: lidarr, needs-love, activiteit
editor: markdown
dateCreated: 2021-06-14T21:35:25.390Z
---

# Activiteit

Het tabblad Activiteit is waar je alle activiteiten van \*Arr kunt zien, zowel vroeger als nu. Dit omvat imports, verwijderingen, upgrades, downloads, hernoemingen en mislukkingen.

# Wachtrij

Wanneer iets actief wordt gedownload en nog niet geïmporteerd in \*Arr, wordt dit weergegeven op de Wachtrij-pagina.

De wachtrij toont alle items die de applicatie kan herkennen en die zich bevinden in de categorie van de opgegeven downloadclient (Instellingen => Downloadclient => Categorie). Om alle releases te bekijken, ga naar Opties => Onbekende weergeven. De wachtrij wordt niet opgeslagen binnen de applicatie, maar wordt bijgewerkt via de API-responses van je downloadclient.

> Voor Usenet-clients zal \*Arr slechts 60 items diep in de wachtrij kijken voor potentiële imports! Het is belangrijk om dit niet te overschrijden, anders moet je handmatig imports opruimen wanneer je systeem overbelast raakt en items mist!.
> Verwijder voltooide downloads moet ook ingeschakeld zijn voor je downloadclient. {.is-warning}

## Pictogrammen voor wachtrijacties

- X - Item uit de wachtrij verwijderen
  - Release verwijderen uit downloadclient - Release verwijderen uit de downloadclient. Verplicht voor niet-overeenkomende release-items
  - Release op de blokkeerlijst plaatsen - Release toevoegen aan de blokkeerlijst
- Pictogram van een persoon - Handmatige import van release
- Pictogram van een hand - Release naar downloadclient sturen

## Wachtrijstatussen

> Let op: het onderstaande is onvolledig {.is-warning}

| Pictogram       | Status                   | Beschrijving                                                                                     | Oplossingsstappen                                         |
| ---------- | ------------------------ | ----------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Grijze klok | Release in afwachting          | Download wacht op beschikbaarheid van de downloadclient of op het voldoen aan de regels van het vertragingsprofiel | N.V.T.                                                      |
| Geel     | Waarschuwing: importeren niet mogelijk | \*Arr kon de release niet importeren. Bekijk de tooltip voor meer details                    | [Raadpleeg de Probleemoplossingsgids](/lidarr/troubleshooting) |
| Paars     | Download wordt geïmporteerd       | Download wordt geïmporteerd                                                                           | N.V.T.                                                      |
|            |                          |                                                                                                 |                                                          |
|            |                          |                                                                                                 |                                                          |

# Geschiedenis

Het tabblad Geschiedenis toont alle taken die de wachtrij hebben verlaten omdat ze zijn voltooid/beëindigd. Dit omvat imports, mislukkingen, downloads, verwijderingen en upgrades.

Het linkericoon is de actie die is uitgevoerd (de lijst met mogelijke acties wordt hieronder weergegeven). Je kunt deze filteren door op het filterpictogram aan de rechterkant te klikken. Je kunt ook meer kolommen weergeven door op Opties te klikken.

![history2.png](/assets/lidarr/history2.png)

Bij de statussen 'Gedownload' kun je op het informatiepictogram aan de rechterkant klikken om meer details over de download te zien (van welke indexer deze afkomstig is, de URL van de download, de leeftijd van de upload, enz.). Je kunt dit item ook markeren als mislukt om een verwijdering, blokkering en opnieuw zoeken van het item te starten.

![history4.png](/assets/lidarr/history4.png)

# Blokkeerlijst

> De blokkeerlijst heette voorheen 'Zwarte lijst' {.is-info}

Op de blokkeerlijstpagina zie je items die zijn geblokkeerd, zodat ze niet opnieuw worden gedownload. Dit zijn mislukkingen uit het automatische proces of handmatig gemarkeerde mislukte items. Items blijven voor altijd op de blokkeerlijst staan, tenzij je ze handmatig verwijdert.

![blocklist1.png](/assets/lidarr/blocklist1.png)

Door op het informatiepictogram aan de rechterkant te klikken, kun je meer details zien over de geblokkeerde invoer en of deze handmatig als mislukt is gemarkeerd of automatisch is mislukt tijdens het downloaden.

![blocklist2.png](/assets/lidarr/blocklist2.png)

Door op het kruisje aan de rechterkant te klikken, wordt het item van de blokkeerlijst verwijderd, zodat je het eventueel opnieuw kunt downloaden als het per ongeluk is toegevoegd.

## Veelvoorkomende redenen voor blokkering

- Gebruiker heeft download handmatig als mislukt gemarkeerd
- Gebruiker heeft "Toevoegen aan blokkeerlijst" geselecteerd bij het verwijderen uit de wachtrij
- Usenet-downloadclient heeft een mislukte download van de release gemeld