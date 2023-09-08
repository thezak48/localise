---
title: Sonarr Bijdragen
description: 
published: true
date: 2023-09-03T13:55:05.394Z
tags: sonarr
editor: markdown
dateCreated: 2021-06-11T23:10:04.820Z
---

# Hoe bij te dragen

We zijn altijd op zoek naar mensen die willen helpen om Sonarr nog beter te maken. Er zijn verschillende manieren om bij te dragen.

# Documentatie

Installatiehandleidingen, [FAQ](/sonarr/faq), hoe meer informatie we hebben op de [wiki](https://wiki.servarr.com/sonarr), hoe beter.

# Ontwikkeling

Sonarr is geschreven in C# (backend) en JS (frontend). De backend is gebouwd op het .NET6-framework, terwijl de frontend gebruikmaakt van Reactjs.

## Vereiste tools

- Visual Studio 2022 of hoger wordt aanbevolen (<https://www.visualstudio.com/vs/>). De communityversie is gratis en werkt (<https://www.visualstudio.com/downloads/>).

> VS 2022 V17.0 of hoger wordt aanbevolen, omdat het de .NET6 SDK bevat
{.is-info}

- HTML/Javascript-editor naar keuze (VS Code/Sublime Text/Webstorm/Atom/etc)
- [Git](https://git-scm.com/downloads)
- De [Node.js](https://nodejs.org/) runtime is vereist. De volgende versies worden ondersteund:
  - **12.0** of hoger
  - **14.0** of hoger
  - **16.0** of hoger
{.grid-list}

> Sonarr werkt **NIET** op oudere versies zoals `10.x`, `8.x`, `6.x`, of elke versie onder 12.0!
{.is-warning}

- [Yarn](https://yarnpkg.com/getting-started/install) is vereist om de frontend te bouwen
  - Yarn is standaard inbegrepen bij **Node 16.10**+. Schakel het in met `corepack enable`
  - Voor andere Node-versies installeer je het met `npm i -g corepack`

## Aan de slag

1. Fork Sonarr
1. Kloon de repository naar je ontwikkelmachine. [*info*](https://docs.github.com/en/get-started/quickstart/fork-a-repo)

> Zorg ervoor dat je `yarn lint --fix` uitvoert op je code voor eventuele wijzigingen aan de frontend voordat je commit.
Voor css-wijzigingen `yarn stylelint-windows --fix` {.is-info}

### Het bouwen van de frontend

- Navigeer naar de gekloonde directory
- Installeer de vereiste Node Packages

     ```bash
     yarn install
     ```

- Start webpack om je ontwikkelomgeving te bewaken op wijzigingen die post-processing vereisen met behulp van:

     ```bash
     yarn start
     ```

### Het bouwen van de backend

De backend-oplossing kan het gemakkelijkst worden gebouwd en uitgevoerd in Visual Studio of Rider. Als de prioriteit echter alleen ligt bij het werken aan de frontend-UI, kan deze ook eenvoudig vanaf de opdrachtregel worden gebouwd wanneer de juiste SDK is geïnstalleerd.

#### Visual Studio

> Zorg ervoor dat het opstartproject is ingesteld op `Sonarr.Console` en het framework op `net6.0`
{.is-info}

1. Bouw eerst de oplossing in Visual Studio, dit zorgt ervoor dat alle projecten correct worden gebouwd en afhankelijkheden worden hersteld
1. Start vervolgens het project in Visual Studio op voor debuggen/uitvoeren om Sonarr te starten
1. Open <http://localhost:8989>

#### Opdrachtregel

1. Maak de oplossing schoon

  ```shell
  dotnet clean $slnFile -c Debug
  ```

1. Herstel en bouw de debugconfiguratie voor het juiste platform (Posix of Windows)

```shell
dotnet msbuild -restore src/Sonarr.sln -p:Configuration=Debug -p:Platform=Posix -t:PublishAllRids
```

1. Voer het geproduceerde uitvoerbare bestand uit vanuit `/_output`

## Code bijdragen

- Als je een nieuwe, al gevraagde functie toevoegt, reageer dan op [GitHub Issues](https://github.com/Sonarr/Sonarr/issues) zodat het werk niet wordt gedupliceerd (Als je iets wilt toevoegen dat nog niet op de lijst staat, praat dan eerst met ons)
- Rebase vanaf de ontwikkelingsbranch van Sonarr, voer geen merge uit
- Maak betekenisvolle commits of squash ze
- Voel je vrij om een pull request te maken voordat het werk is voltooid, dit stelt ons in staat om te zien waar het zich bevindt en opmerkingen te maken/verbeteringen voor te stellen
- Neem contact met ons op via Discord als je vragen hebt
- Voeg tests toe (unit/integratie)
- Commit met \*nix-regelafbrekingen voor consistentie (We controleren uit op Windows en committen met \*nix)
- Eén functie/bugfix per pull request om het overzichtelijk en gemakkelijk te begrijpen te houden
- Gebruik 4 spaties in plaats van tabs, dit is de standaardinstelling voor VS 2022 en WebStorm

## Pull-aanvragen

- Maak alleen pull-aanvragen naar `develop`, nooit naar `main`, als je een PR maakt naar `main`, zullen we erop reageren en deze sluiten
- Je krijgt waarschijnlijk opmerkingen of vragen van ons, deze zijn bedoeld om consistentie en onderhoudbaarheid te waarborgen
- We proberen zo snel mogelijk te reageren op pull-aanvragen, als het al een dag of twee geleden is, neem dan contact met ons op via Discord, we hebben het misschien gemist
- Elke PR moet afkomstig zijn van zijn eigen [feature-branch](http://martinfowler.com/bliki/FeatureBranch.html) en niet van de ontwikkelingsbranch in je fork, het moet een betekenisvolle naam hebben (wat wordt er toegevoegd/hersteld)
  - `new-feature` (Goed)
  - `fix-bug` (Goed)
  - `patch` (Slecht)
  - `develop` (Slecht)
- Commits moeten worden geschreven als `New:` of `Fixed:` voor wijzigingen die niet als een `onderhoudsrelease` worden beschouwd

## Unit Testing

Sonarr maakt gebruik van nunit voor zijn unit-, integratie- en automatiseringstestsuite.

### Het uitvoeren van tests

Tests kunnen eenvoudig worden uitgevoerd vanuit VS met behulp van het meegeleverde nunit3testadapter-nuget-pakket of vanaf de opdrachtregel met behulp van het meegeleverde bash-script `test.sh`.

Navigeer in VS eenvoudig naar Test Explorer en voer de tests uit of debug de tests die je wilt onderzoeken.

Tests kunnen allemaal tegelijkertijd of één voor één worden uitgevoerd in VS.

Vanaf de opdrachtregel accepteert het script `test.sh` 3 parameters

```bash
test.sh <PLATFORM> <TYPE> <COVERAGE>
```

### Het schrijven van tests

Hoewel het niet altijd leuk is, moedigen we het schrijven van unit tests aan voor elke wijziging in de backendcode. Dit zorgt ervoor dat de wijziging werkt zoals bedoeld en dat toekomstige wijzigingen de verwachte werking niet verstoren.

> We vereisen momenteel 80% dekking voor nieuwe code bij het indienen van een PR
{.is-info}

Als je vragen hebt over een van deze punten, laat het ons dan weten.

# Vertaling

Sonarr maakt gebruik van een zelf gehoste open toegankelijke [Weblate](https://translate.servarr.com)-instantie om zijn json-vertaalbestanden te beheren. Deze bestanden worden opgeslagen in de repo op `src/NzbDrone.Core/Localization`

## Bijdragen aan een bestaande vertaling

Weblate zorgt voor synchronisatie en vertaling van strings voor alle talen, behalve Engels. Het bewerken van vertaalde strings en het vertalen van bestaande strings voor ondersteunde talen moet daar worden uitgevoerd voor het Sonarr-project.

De Engelse vertaling, `en.json`, dient als bron voor alle andere vertalingen en wordt beheerd op de GitHub-repo.

## Het toevoegen van een taal

Het toevoegen van vertalingen aan Sonarr vereist twee stappen

- Het toevoegen van de taal aan weblate
- Het toevoegen van de taal aan de Sonarr-codebase

## Het toevoegen van vertaalstrings in de code

De Engelse vertaling, `src/NzbDrone.Core/Localization/en.json`, dient als bron voor alle andere vertalingen en wordt beheerd op de GitHub-repo. Bij het toevoegen van een nieuwe string aan zowel de UI als de backend moet ook een sleutel worden toegevoegd aan `en.json`, samen met de standaardwaarde in het Engels. Deze sleutel kan vervolgens als volgt worden gebruikt:

> PR's voor vertaling van logberichten worden niet geaccepteerd
{.is-warning}

### Backend-strings

Backend-strings kunnen worden toegevoegd met behulp van de Localization Service `GetLocalizedString`-methode

```dotnet
private readonly ILocalizationService _localizationService;

public IndexerCheck(ILocalizationService localizationService)
{
  _localizationService = localizationService;
}
        
var translated = _localizationService.GetLocalizedString("IndexerHealthCheckNoIndexers")
```

### Frontend-strings

Nieuwe strings kunnen aan de frontend worden toegevoegd door de translate-functie te importeren en een sleutel te gebruiken die is gespecificeerd in `en.json`

```js
import translate from 'Utilities/String/translate';

<div>
  {translate('UnableToAddANewIndexerPleaseTryAgain')}
</div>
```